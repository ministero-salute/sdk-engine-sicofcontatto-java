# sdk-engine-sicofcontatto-java

## Sistema informativo Consultori Familiari Contatto

### Descrizione repository:

Il microservizio ha come scopo l’acquisizione dei dati inviati dalle Regioni in merito alle prestazioni consultoriali previste dall’articolo 24 «Assistenza sociosanitaria ai minori, alle donne, alle coppie, alle famiglie» DPCM 12 gennaio 2017 (Nuovi LEA).

I dati richiesti sono relativi al set di informazioni individuali riguardanti le attività consultoriali, a favore degli assistiti residenti e non residenti nel territorio italiano. Il tracciato SICOF_CONTATTO comprende le informazioni relative ai dati anagrafici dell’assistito che accede al consultorio e quindi dello specifico contatto.

Il Sistema viene alimentato con le informazioni relative all’attività dei Consultori Familiari a partire dai dati attinenti al secondo semestre 2023 con cadenza SEMESTRALE

L'invio dei file viene effettuato mediante un tracciato XML.
Per ogni tracciato XML, è fornito il relativo schema XSD di convalida a cui far riferimento

#### Struttura XML:

Evento:
- Contatto

Nodi di riferimento Contatto:
- Trasmissione 
- Dati Anagrafici
- Assistito
- Residenza  
- Erogatore
- Contatto  

Campi Trasmissione :
- Tipo     

Campi Dati Anagrafici: 
- CUNI 
- ValiditàCI
- TipologiaCI 
- AnnoNascita
- Genere
- Cittadinanza 
- StatoCivile
- CondProfessionale
- TitoloStudio
- ComuneNascita


Campi Assistito
- Servizio
- PartecEventGruppo


Campi Residenza:
- RegioneRes
- CodASLRes
- ComuneRes

Campi Erogatore:
- CodRegioneErg (campo chiave)
- CodASLErg (campo chiave)
- CodConsultorio (campo chiave)

Campi Contatto:
- Data (campo chiave)
- SoggRichiedente
- IdAccesso (campo chiave)
- IdNucleo (campo chiave)



## 📚 XSD di riferimento
Il file xsd è disponibile al percorso [`docs/FlsSicof_1.xsd`](docs/FlsSicof_1.xsd).



### Struttura repository

La cartella principale è src/main/java che è organizzata nelle seguenti cartelle:

- it.mds.sdk.engine.config che raccoglie i file di configurazione
- it.mds.sdk.flusso.sicof.contatto che contiene il file necessario all'avvio dell'applicazione
- it.mds.sdk.flusso.sicof.contatto.controller che contiene i file che vengono invocati direttamente dal client
- it.mds.sdk.flusso.sicof.contatto.dto che contiene le classi che rappresentano il modello interno di sdk
- it.mds.sdk.flusso.sicof.contatto.mapper che contiene le classi di conversione

Nella cartella src/main/resources sono presenti le seguenti cartelle:
- META-INF che contiene file di configurazione
- sicof xhe contiene file .moustache
- template contiene file .csv, .xml e .xsd

sono presenti in resources anche file di configurazione:
- application.yaml
- config-flusso.properties
- csvHeaderMapping.properties
- logback-spring.xml
- tmp.xml

è presente il file pom.xml (Project Object Model), è un file XML che contiene le informazioni sul progetto e dettagli sulle configurazioni utilizzate da Maven per eseguire la build del progetto

### Prerequisiti e dipendenze

Il microservizio può girare su qualsiasi sistema operativo per cui è prevista una JVM (Java Virtual Machine) e utilizza la versione 2.7.17 di Spring Boot.
## Istruzioni per l'installazione

Per l'installazione e l'avvio dell'engine seguire la documentazione tecnica dettagliata disponibile all'url [`INSTALL.md`](https://github.com/ministero-salute/sdk-utilities-regole-properties/blob/main/INSTALL.md).

## 📝 Licenza
Questo progetto è rilasciato sotto licenza BSD 3-Clause License così come definita [BSD 3-Clause License](./LICENSE).

## 🤝 Contributi
I contributi sono benvenuti. Si prega di consultare il file [`CONTRIBUTING.md`](CONTRIBUTING.md) per le linee guida su come contribuire al progetto.

## 📞 Contatti
Per ulteriori informazioni, contattare:

- **Service Desk - Ministero della Salute**: servicedesk.mds@medilifegroupspa.com
- **Amministrazione titolare**: [Ministero della Salute](https://www.salute.gov.it)

## mantainer:
 Accenture SpA until January 2026
