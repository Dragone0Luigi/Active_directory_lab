# 🏢 Active Directory Enterprise Home Lab

![Windows Server](https://img.shields.io/badge/Windows_Server-2022-0078D6?style=for-the-badge&logo=windows-server&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active_Directory-Domain_Services-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Group Policy](https://img.shields.io/badge/GPO-Group_Policy-orange?style=for-the-badge)
![Windows 10](https://img.shields.io/badge/Windows_10-Enterprise-0078D4?style=for-the-badge&logo=windows10&logoColor=white)

Laboratorio pratico di simulazione aziendale per la progettazione, configurazione e testing di un ambiente basato su **Active Directory Domain Services (AD DS)**, **Group Policy Objects (GPO)** e **Condivisioni di Rete con Sicurezza Basata su Ruoli (RBAC)**.

---

## 🛠️ Phase 1: Setup Base e Promozione Server

Configurazione iniziale dell'ambiente server, impostazione della rete e promozione del server a **Domain Controller** principale.

### 1.1 Inizializzazione Server

|       Step 1: Lingua e Regione        |    Step 2: Inserimento Product Key    |
| :-----------------------------------: | :-----------------------------------: |
| ![Setup 1]([server/Setup_server_1.png](https://github.com/Dragone0Luigi/Active_directory_lab/blob/main/Active_directory_lab/Docs/server/Setup_server_1.png
)) | ![Setup 2](server/Setup_server_2.png) |

|      Step 3: Selezione OS (GUI)       |     Step 4: Partizionamento Disco     |
| :-----------------------------------: | :-----------------------------------: |
| ![Setup 3](server/Setup_server_3.png) | ![Setup 4](server/Setup_server_4.png) |

### 1.2 Rete e Installazione Ruoli AD DS

1. Impostazione IP Statico e configurazione DNS locale su Server.
2. Aggiunta dei ruoli **Active Directory Domain Services** e **DNS Server**.
3. Promozione del server con creazione della nuova foresta di dominio.

|                    IP Statico & DNS                    |                  Installazione Ruoli                  |                   Dettaglio Funzionalità                    |                     Promozione Foresta                     |
| :----------------------------------------------------: | :---------------------------------------------------: | :---------------------------------------------------------: | :--------------------------------------------------------: |
| ![IP Statico](server/configurazione_ip_dns_server.png) | ![Ruoli AD DS](server/installazione_ruoli_ad_dns.png) | ![Dettagli AD DS](server/dettaglio_funzionalita_ad_dns.png) | ![Creazione Foresta](server/creazione_foresta_dominio.png) |

---

## 👥 Phase 2: Organizzazione AD (OU, Utenti e Gruppi)

Creazione dell'albero delle **Organizational Units (OU)** e implementazione del modello di sicurezza per la gestione degli utenti e dei gruppi dipartimentali.

### 2.1 Struttura delle OU (Organizational Units)

- **OU Principale**: Strutturazione delle macro-aree aziendali.
- **OU Dipartimentali**: Creazione della struttura specifica per il reparto IT.

|                   Creazione OU Principale                    |                Creazione OU Reparto IT                |
| :----------------------------------------------------------: | :---------------------------------------------------: |
| ![Creazione OU AD](server/creazione_ou_active_directory.png) | ![Creazione OU IT](server/creazione_ou_repartoit.png) |

### 2.2 Utenti e Gruppi di Sicurezza

- Creazione dell'utente responsabile/manager.
- Popolamento dei gruppi **Backend** e **Frontend** per il controllo accessi granulare.

|                      Utente Manager / Admin                      |                        Gruppo Backend                         |                         Gruppo Frontend                         |
| :--------------------------------------------------------------: | :-----------------------------------------------------------: | :-------------------------------------------------------------: |
| ![Utente Responsabile](server/creazione_utente_responsabile.png) | ![Gruppo Backend](server/creazione_gruppo_utente_backend.png) | ![Gruppo Frontend](server/creazione_gruppo_utente_frontend.png) |

---

## ⚙️ Phase 3: Configurazione Group Policy (GPO)

Applicazione e test delle **Group Policy Objects** a livello di Dominio/OU per garantire la sicurezza e la conformità delle workstation.

- **Windows Update GPO**: Automazione della gestione degli aggiornamenti.
- **Firewall & RDP**: Configurazione centralizzata delle regole di Firewall e abilitazione del Remote Desktop.

|                  GPO Windows Update                  |                 Verifica Applicazione GPO                  |                GPO Firewall & Remote Desktop                |
| :--------------------------------------------------: | :--------------------------------------------------------: | :---------------------------------------------------------: |
| ![GPO Windows Update](server/gpo_windows_update.png) | ![Verifica GPO WU](server/verifica_gpo_windows_update.png) | ![GPO Firewall RDP](server/gpo_firewall_remote_desktop.png) |

---

## 💻 Phase 4: Integration Client & Join Dominio

Configurazione delle postazioni di lavoro client per la comunicazione con il Domain Controller e onboarding della macchina aziendale.

1. Configurazione del client e puntamento del DNS verso l'IP del Server DC.
2. Esecuzione del **Domain Join** tramite credenziali amministrative/Lead.

|            Preparation Client            |              Configurazione DNS Client              |               Join al Dominio (Account Lead)               |                Dominio Connesso                |
| :--------------------------------------: | :-------------------------------------------------: | :--------------------------------------------------------: | :--------------------------------------------: |
| ![Setup Client](client/setup_client.png) | ![DNS Client](client/configurazione_dns_client.png) | ![Join Lead Account](Client/join_dominio_account_lead.png) | ![Join Client](client/join_dominio_client.png) |

---

## 🔒 Phase 5: Permessi Condivisione & Audit Accessi (RBAC)

Configurazione delle cartelle condivise di rete (Network Shares) con permessi **NTFS e Share** assegnati ai gruppi Active Directory.

### 5.1 Definizione Permessi di Condivisione

|                 Permessi Cartella Backend                  |                  Permessi Cartella Frontend                  |                Permessi Cartella Lead                |
| :--------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------------------------: |
| ![Share Backend](server/permessi_condivisione_backend.png) | ![Share Frontend](server/permessi_condivisione_frontend.png) | ![Share Lead](server/permessi_condivisione_lead.png) |

### 5.2 Verification & Security Testing

Verifica dell'efficacia delle politiche di sicurezza provando l'accesso con diversi profili utente:

|           Test Accesso Riuscito (Utente Autorizzato)           |                  Test Accesso Negato (Security Audit)                  |
| :------------------------------------------------------------: | :--------------------------------------------------------------------: |
| ![Accesso Riuscito](Client/accesso_riuscito_cartella_lead.png) |       ![Accesso Negato](Client/test_accesso_negato_permessi.png)       |
|  _L'utente autorizzato del gruppo Lead accede alla cartella._  | _L'accesso viene bloccato dal sistema per gli utenti non autorizzati._ |
