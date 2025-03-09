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



XSD:
```
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://flussi.mds.it/FlsSicof_1" xmlns:fls="http://flussi.mds.it/FlsSicof_1" xmlns:xs="http://www.w3.org/2001/XMLSchema">
	<xs:simpleType name="TipoTrasmissione">
		<xs:restriction base="xs:string">
			<xs:pattern value="[IVC]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="IdAccesso">
		<xs:restriction base="xs:positiveInteger">
			<xs:maxInclusive value="99999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="IdNucleo">
		<xs:restriction base="xs:positiveInteger">
			<xs:maxInclusive value="9999999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="CUNI">
		<xs:restriction base="xs:string">
			<xs:length value="88"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="ValiditaCI">
		<xs:restriction base="xs:integer">
			<xs:pattern value="[0-1]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="TipologiaCI">
		<xs:restriction base="xs:integer">
			<xs:enumeration value="0"/>
			<xs:enumeration value="1"/>
			<xs:enumeration value="2"/>
			<xs:enumeration value="3"/>
			<xs:enumeration value="4"/>
			<xs:enumeration value="97"/>
			<xs:enumeration value="98"/>
			<xs:enumeration value="99"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="AnnoNas">
		<xs:restriction base="xs:int">
			<xs:minInclusive value="1899"/>
			<xs:maxInclusive value="2099"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="ComuneNas">
		<xs:restriction base="xs:string">
			<xs:pattern value="999999"/>
			<xs:pattern value="[a-zA-Z0-9]{6}"/>
			<xs:pattern value="99Z999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="Genere">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="NucleoFamiliare">
		<xs:restriction base="xs:int">
			<xs:minInclusive value="0"/>
			<xs:maxInclusive value="99"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="Cittadinanza">
		<xs:restriction base="xs:string">
			<xs:pattern value="[A-Z]{2}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="StatoCivile">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-9]{1}"/>
			<xs:pattern value="10"/>
			<xs:pattern value="99"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="CondProfessionale">
		<xs:restriction base="xs:int">
			<xs:pattern value="[1-7]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="TitoloStudio">
		<xs:restriction base="xs:int">
			<xs:pattern value="[1-7]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="RegioneResidenza">
		<xs:restriction base="xs:string">
			<xs:pattern value="010"/>
			<xs:pattern value="020"/>
			<xs:pattern value="030"/>
			<xs:pattern value="041"/>
			<xs:pattern value="042"/>
			<xs:pattern value="050"/>
			<xs:pattern value="060"/>
			<xs:pattern value="070"/>
			<xs:pattern value="080"/>
			<xs:pattern value="090"/>
			<xs:pattern value="100"/>
			<xs:pattern value="110"/>
			<xs:pattern value="120"/>
			<xs:pattern value="130"/>
			<xs:pattern value="140"/>
			<xs:pattern value="150"/>
			<xs:pattern value="160"/>
			<xs:pattern value="170"/>
			<xs:pattern value="180"/>
			<xs:pattern value="190"/>
			<xs:pattern value="200"/>
			<xs:pattern value="999"/>
			<xs:pattern value="[A-Z]{3}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="CodASLResidenza">
		<xs:restriction base="xs:string">
			<xs:length value="3"/>
			<xs:pattern value="[0-9]{3}"/>
			<xs:pattern value="999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="ComuneRes">
		<xs:restriction base="xs:string">
			<xs:pattern value="999999"/>
			<xs:pattern value="[a-zA-Z0-9]{6}"/>
			<xs:pattern value="99Z999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="SoggettoRichiedente">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-9]{1}"/>
			<xs:pattern value="10"/>
			<xs:pattern value="11"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="RegioneErogazione">
		<xs:restriction base="xs:string">
			<xs:pattern value="010"/>
			<xs:pattern value="020"/>
			<xs:pattern value="030"/>
			<xs:pattern value="041"/>
			<xs:pattern value="042"/>
			<xs:pattern value="050"/>
			<xs:pattern value="060"/>
			<xs:pattern value="070"/>
			<xs:pattern value="080"/>
			<xs:pattern value="090"/>
			<xs:pattern value="100"/>
			<xs:pattern value="110"/>
			<xs:pattern value="120"/>
			<xs:pattern value="130"/>
			<xs:pattern value="140"/>
			<xs:pattern value="150"/>
			<xs:pattern value="160"/>
			<xs:pattern value="170"/>
			<xs:pattern value="180"/>
			<xs:pattern value="190"/>
			<xs:pattern value="200"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="CodASLErogazione">
		<xs:restriction base="xs:string">
			<xs:length value="3"/>
			<xs:pattern value="[0-9]{3}"/>
			<xs:pattern value="999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="CodiceConsultorioErogazione">
		<xs:restriction base="xs:string">
			<xs:length value="6"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="CodServizio">
		<xs:restriction base="xs:int">
			<xs:pattern value="[01-4]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="PartecEventoGruppo">
		<xs:restriction base="xs:int">
			<xs:pattern value="[1-5]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="StatoEstero">
		<xs:restriction base="xs:string">
			<xs:pattern value="[A-Za-z]{2}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="Data_F">
		<xs:restriction base="xs:string">
			<xs:pattern value="(0[1-9]|[12][0-9]|3[01])-(0[1-9]|1[012])-(19|20)\d\d(19|20)\d\d-(0[1-9]|1[012])-(0[1-9]|[12][0-9]|3[01])"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:element name="Trasmissione">
		<xs:complexType>
			<xs:attribute name="Tipo" type="fls:TipoTrasmissione" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Assistito">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:DatiAnagrafici"/>
				<xs:element name="Servizio" type="fls:CodServizio"/>
				<xs:element name="PartEventoGruppo" type="fls:PartecEventoGruppo" nillable="false" minOccurs="0"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="DatiAnagrafici">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="CUNI" type="fls:CUNI"/>
				<xs:element name="validitaCI" type="fls:ValiditaCI"/>
				<xs:element name="tipologiaCI" type="fls:TipologiaCI"/>
				<xs:element name="AnnoNascita" type="fls:AnnoNas"/>
				<xs:element name="Genere" type="fls:Genere"/>
				<xs:element name="Cittadinanza" type="fls:Cittadinanza"/>
				<xs:element name="StatoCivile" type="fls:StatoCivile"/>
				<xs:element name="CondProfessionale" type="fls:CondProfessionale"/>
				<xs:element name="TitoloStudio" type="fls:TitoloStudio"/>
				<xs:element ref="fls:Residenza"/>
			</xs:sequence>
			<xs:attribute name="ComuneNascita" type="fls:ComuneNas" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Erogazione">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="CodRegioneErg" type="fls:RegioneErogazione"/>
				<xs:element name="CodASLErg" type="fls:CodASLErogazione"/>
				<xs:element name="CodConsultorio" type="fls:CodiceConsultorioErogazione"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="FlsSicof_1">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:Contatto" maxOccurs="unbounded"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Residenza">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="RegioneRes" type="fls:RegioneResidenza"/>
				<xs:element name="CodASLRes" type="fls:CodASLResidenza" nillable="false" minOccurs="1"/>
				<xs:element name="ComuneRes" type="fls:ComuneRes"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Contatto">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:Trasmissione"/>
				<xs:element ref="fls:Assistito"/>
				<xs:element ref="fls:Erogazione"/>
			</xs:sequence>
			<xs:attribute name="Data" type="fls:Data_F" use="required"/>
			<xs:attribute name="SoggRichiedente" type="fls:SoggettoRichiedente" use="required"/>
			<xs:attribute name="IdAccesso" type="fls:IdAccesso" use="required"/>
			<xs:attribute name="IdNucleo" type="fls:IdNucleo" use="optional"/>
		</xs:complexType>
	</xs:element>
</xs:schema>
```

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

### Istruzioni per l'installazione

Per poter eseguire la build: 
build system maven,
comando mvn clean package

Per eseguire l'installazione è necessario prendere il jar generato dal build system e copiarlo in una cartella, successivamente all'interno della root folder ( / su Linux mentre C:\ su Windows) creare la cartella sdk e tutte le sottocartelle e i file necessari:
```
 /
 +- sdk
   +- db - la directory in cui viene genrato il db sqllite per la storicizzazione dele anagrafiche
   +- dir - la directory in cui inserire i csv da validare e inviare
   +- esiti - la directory in cui verranno depositati i file con gli esiti delle esecuzioni dell'sdk
   +- log - la directory in cui verranno scritti i log delll'applicativo
   +- progressivo - la directory in cui l'applicativo mantiene un file dat per la generazione degli id di esecuzione
   +- properties - la directory contenente i file di configurazione dell'sdk
      +- config-flusso.properties - file di configurazione principale (da referenziare in fase di avvio)  
      \- configurazioni-anagrafiche.properties - file per la configurazione del recupero delle anagrafiche 
   +- regole - la directory contenente le regole da applicare ai csv
   +- run - la cartella contenente i file di run per ogni singola esecuzione
   +- xmloutput - la directory contenente gli xml di output
   \- sent - la directory in cui vengono spostati gli xml inviati al ministero
``` 
- #### config-flusso.properties
```
nome.flusso=<nome del flusso lato ministero>
flusso.categoria=<categoria del flusso lato ministero>
flusso.codifica=<codice identificativo del flusso lato ministero>
regole.percorso=<path completo al file xml delle regole: /sdk/regole/regole.xml>

xmloutput.percorso=<path completo della folder in cui scrivere l'output>/SDK_{{periodoRiferimento}}_{{idRun}}.xml (/sdk/xmloutput/SDK_{{periodoRiferimento}}_{{idRun}}.xml)

sent.percorso=<path completo della directory in cui spostare gli xml inviati al ministero: /sdk/sent/>
flusso.percorso=<path completo della directory in cui verranno depositati i file csv: /sdk/dir/>
soglia.invio.mds=<numero intero indicante quanti la soglia di record validi per file affinché possa essere inviato l'xml di output: 100>
separatore=<carattere di separazione dei valori nel csv: ~>

run.percorso=<path completo della directory in storicizzare i file di run: /sdk/run>
esito.percorso=<path completo della directory in cui depositare i file di esito: /sdk/esiti>
progressivo.percorso=<path completo della directory in cui generare il file dat dei progressivi: /sdk/progressivo>

url.rest.gaf=<url per l'invio degli xml: https://api.salute.gov.it/api/gaf/upldfunc>
gaf.sender.authorizer.token-issuer.url=<url per l'autenticazione dell'invio: https://nsis-ids.sanita.it/nidp/oauth/nam/token>
gaf.sender.authorizer.token-issuer.grant_type=<flow di autenticazione: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.username=<username: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.password=<password: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.client_id=<client id: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.client_secret=<client secret: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.scope=<scopes a cui deve appartenere l'utente: verranno forniti dal ministero>
gaf.sender.authorizer.type=<tipo di token di autenticazione: JWT>
gaf.sender.type=REST
gaf.sender.fileType=<categoria del flusso: valorizzare come flusso.categoria>
```

- #### configurazioni-anagrafiche.properties
```
sqlite.database.file.path=<path completo in cui creare il db sqllite: /sdk/db/anagrafica.db>
resilienza.ore=<time to live delle anagrafiche nel DB in ore: 2>

client.rest.headers.x-pplication-id: APP_ID_REGISTRYDOWNLOADER_CLIENT
client.type=REST
client.host=<url del gestore anagrafi: https://api.salute.gov.it/api/gestanag/v1>

rest.authorizer.type=<tipo del token di autorizzazione/autenticazione: JWT>
rest.authorizer.token-issuer.url=<url per la generazione di un token di autenticazione: https://nsis-ids.sanita.it/nidp/oauth/nam/token>
rest.authorizer.token-issuer.grant_type=<tipo di flow da utilizzare per l'autenticazione: client_credentials>
rest.authorizer.token-issuer.username=<username: verrà fornita dal ministero>
rest.authorizer.token-issuer.password=<password: verrà fornita dal ministero>
rest.authorizer.token-issuer.client_id=<client id: verrà fornita dal ministero>
rest.authorizer.token-issuer.client_secret=<client secret: verrà fornita dal ministero>
rest.authorizer.token-issuer.scope=<scopes a cui deve appartenere l'utenza: verrà fornita dal ministero>
```

### Istruzioni di avvio

Per avviare l'applicativo eseguire il seguente comando
```
java -jar <path completo del jar> --config=<path completo al file di configurazione principale>
```
Il comando farà partire il software che rimarrà in attesa di richieste sulla porta 8080

#### Avvio validazione di un csv
```
curl --location --request POST 'http://localhost:8080/v1/flusso/SICOF_CONTATTO' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--data-raw '{
    "nomeFile": "test.csv",
    "idClient": "1663" ,
    "modalitaOperativa":"P",
    "annoRiferimento": "2022",
    "periodoRiferimento": "13",
    "codiceRegione": "120"
}'
```

#### Recupero dell'esito di un'elaborazione
```
curl --location --request GET 'http://localhost:8080/v1/flusso/SICOF_CONTATTO/info?idRun=34' --header 'Accept: */*'
```

### Detentori di copyright

### Incaricati del mantenimento del progetto open source

### Contatti per segnalazioni

## mantainer:
Accenture SpA until January 2026

