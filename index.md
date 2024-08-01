---
layout: default
---

### Contesto attuale

La sicurezza stradale e l'efficienza nella guida dei veicoli sono temi di crescente importanza nel contesto delle moderne tecnologie di mobilità. Con l'incremento dell'adozione di sistemi di monitoraggio e telemetria, è diventato possibile raccogliere una quantità significativa di dati riguardanti il comportamento del veicolo e dello stile di guida. 

### Obiettivi dell'applicativo

**SmartDrive** si pone l'obiettivo di sviluppare un sistema integrato per l'acquisizione, l'analisi e la visualizzazione dei dati di guida, al fine di stimare lo stile di guida del conducente e migliorare la sicurezza e l'efficienza.

### Project team

| Matricola          | Cognome            | Nome               | E-mail                                                                                    |
|:-------------------|:-------------------|:-------------------|:------------------------------------------------------------------------------------------|
| 20090064           | Longo              | Marco              | [marco.longo@studenti.unisalento.it](mailto:marco.longo@studenti.unisalento.it)           |
| 20094004           | Tarantino          | Priamo             | [priamo.tarantino@studenti.unisalento.it](mailto:priamo.tarantino@studenti.unisalento.it) |

### Architettura del sistema

- **Back-end**: Realizzato in _Python_ con l'ausilio del framework _Flask_.
- **Front-end**: Sviluppato con _Vue.js_, con l'ausilio di _Chart.js_ per visualizzare i dati su grafici professionali.
- **Database**: Database NoSQL (_MongoDB_) per lo storage dei dati, strutturato con 4 collezioni: campioni, sessioni, test ed utenti.

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/smartdrive_schema.png" target="_blank">![SmartDrive Schema](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/smartdrive_schema.png)</a>

### Raccolta dati

- **Sensori utilizzati**: Accelerometro, giroscopio e GPS dello smartphone.
- **App di acquisizione**: Utilizzo dell'app _Sensor Logger_ per raccogliere dati in tempo reale ed inviarli al back-end.

### Analisi dei dati

- **Modello di Machine Learning**: Utilizzo del modello _Random Forest_ per classificare lo stile di guida in 4 categorie (prudente, normale, sportivo, aggressivo).
- **Preparazione dei dati**: Pulizia, normalizzazione ed ingegneria delle features per migliorare la precisione del modello.

### Accessibilità della WebApp

- **Registrazione**: La fase di registrazione richiede all'utente: nome, cognome, e-mail, password ed il _Device ID_ del dispositivo in uso (recuperabile nel menù impostazioni dell'app _Sensor Logger_). Hashing delle password degli utenti con _SHA-256_.
- **Login**: Procedura di accesso sicuro tramite autenticazione _JWT_.
- **Area utente**: Gestione del profilo dell'utente. 

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/login_page.png" target="_blank">![Login Page](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/login_page.png)</a>

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/user_area.png" target="_blank">![User Area](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/user_area.png)</a>

### Sessioni di guida

Ogni utente registrato può creare delle sessioni di guida. Una volta alla guida (con l'app _Sensor Logger_ avviata), il back-end recepirà i campioni (raccolti con cadenza di 1 secondo) e li salverà sul DB associandoli alla sessione attiva dell'utente.

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/sessions.png" target="_blank">![Sessions CRUD](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/sessions.png)</a>

### Visualizzazione dei risultati

- **Statistiche generali**: La sezione principale della dashboard mostra le statistiche medie di guida dell'utente relativamente a tutte le sessioni.

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/dashboard_user.png" target="_blank">![Dashboard User](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/dashboard_user.png)</a>

- **Grafici di sessione**: La sezione relativa alle statistiche di sessione mostra svariati grafici per stimare l'andamento puntuale di: _accelerazione_, _velocità_, _rollìo_ e _beccheggio_. Per ogni campione sul grafico è possibile analizzare lo stile di guida istantaneo ad esso associato. Infine è presente una _mappa di geolocalizzazione_ che traccia il percorso effettuato dal guidatore per la sessione in corso.

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/acceleration_speed.png" target="_blank">![Acceleration Speed](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/acceleration_speed.png)</a>

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/pitch_roll.png" target="_blank">![Pitch Roll](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/pitch_roll.png)</a>

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/map_path.png" target="_blank">![Map Path](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/map_path.png)</a>

### Gestione delle collezioni

Nella sezione _Database_ l'utente può caricare con facilità collezioni di dati relative a campioni, sessioni e test. I formati accettati sono <u>.json</u> e <u>.csv</u>.

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/database_upload.png" target="_blank">![Database Upload](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/database_upload.png)</a>

### Processo di validazione

1. **Acquisizione dei dati**: Raccolta di oltre _1.800 campioni_ di dati di guida utilizzando _Sensor Logger_.
2. **Sviluppo del modello**: Addestramento del modello _Random Forest_ con i dati raccolti, ottenendo un'accuratezza del 98.82%.
3. **Analisi dei campioni**: Test su strada per verificare l'affidabilità del sistema nel distinguere diversi stili di guida.
4. **Implementazione delle API**: Creazione di _REST API_ per l'interazione tra front-end e back-end.

<a href="https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/postman_collection.png" target="_blank">![Postman Collection](https://raw.githubusercontent.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-Page-Longo-Tarantino/main/assets/images/postman_collection.png)</a>

### Sviluppi futuri

- **Integrazione di nuove specifiche**: Consumo di carburante, usura dei freni e condizioni ambientali.
- **Espansione a contesti professionali**: Applicazione per aziende di trasporto e conducenti di veicoli pesanti.
- **Tecniche avanzate di ML**: Adattamento a diversi tipi di veicoli e utilizzo di reti neurali profonde.

### Deploy locale

7 semplici step sono sufficienti per il deploy dell'APP in locale (**Node.js e Python richiesti**):

1. Scaricare la repo del <a href="https://github.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-BackEnd-Longo-Tarantino" target="_blank"><strong>back-end</strong></a>
2. Ripristinare le librerie di Python necessarie con:
```bash
pip install -r requirements.txt
```
3. Ricreare il database dimostrativo con le collezioni presenti in repo:
```bash
mongoimport --db SmartDrive --collection user --file database/SmartDrive.user_final.json --jsonArray
mongoimport --db SmartDrive --collection test --file database/SmartDrive.test_final.json --jsonArray
mongoimport --db SmartDrive --collection samples --file database/SmartDrive.samples_final.json --jsonArray
mongoimport --db SmartDrive --collection session --file database/SmartDrive.session_final.json --jsonArray
```
4. Avviare il back-end (esposto su <u>localhost:8000</u>) con:
```bash
python Server.py
```
5. Scarica la repo del <a href="https://github.com/UniSalento-IDALab-IoTCourse-2023-2024/WoT-SmartDrive-2023-2024-FrontEnd-Longo-Tarantino" target="_blank"><strong>front-end</strong></a>
6. Ripristinare le dipendenze di Node necessarie con:
```bash
npm install
```
7. Avviare il pannello front-end (esposto su <u>localhost:5173</u>) con:
```bash
npm start
```
