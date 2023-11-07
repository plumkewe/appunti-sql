# 🍯 Appunti SQL

Il software che utilizziamo a scuola è:
<p>
<img height="32" width="32" src="https://cdn.simpleicons.org/xampp/orange" alt="XAMPP"/>
</p>
[Scopri di più](https://en.wikipedia.org/wiki/XAMPP)

Gli esercizi saranno disponibili qui:

> **Note**\
> Verrà aggiornato solo quando avrò voglia!

## Contenuti
### [Definizioni](#Definizioni)
* [Database](#Database)
	* [DBMS](#DBMS)
	* [Tipi](#Tipi)
		* Relazionali
		* Non relazionali
* [SQL](#SQL)
* [DDL - Data Definition Language](#)
* [DML - Data Manipulation Language](#Data-Manipulation-Language)
* [DML - Data Control Language](#)
### Data Manipulation Language (DML)
* [Selezione dei dati](#Selezione-dei-dati)
	* [SELECT statement](#SELECT-statement)
		* [Tutte colonne](#Tutte-colonne)
		* [Colonne specifiche](#Colonne-specifiche)
		* [Colonne con alias](#Colonne-con-alias) `AS`
		* [Colonne con espressioni aritmetiche](#Colonne-con-espressioni-aritmetiche)
		* [Seleziona dati univoci (DISTINCT)](#Seleziona-dati-univoci)
	* [Filtraggio dei dati](#Filtraggio-dei-dati)
		* [Corrispondenze parziali o pattern](#Corrispondenze-parziali-o-pattern) `LIKE`
		* [Valore specifico in una colonna](#Valore-specifico-in-una-colonna)
		* [Valore NULL o non NULL](#Valore-NULL-o-non-NULL) `IS NULL`/`IS NOT NULL`
		* [Filtrare utilizzando una lista dei valori](#Filtrare-utilizzando-una-lista-dei-valori) `IN`
	* Operatori di confronto
		* Ugualianza `=`
		* Disugualianza `<>` o `!=`
		* Maggiore di `>`
		* Maggiore o uguale di `>=`
		* Minore `<`
		* Minore o uguale di `=<`
	* Operatori logici
		* AND
		* OR
		* AND e OR
		* NOT
			* Negare condizioni multiple
	* Ordinamento dei risultati `ORDER BY`
	
<br>	
	
## Definizioni
### Database
#### Tipi
##### Relazionali
I database relazionali organizzano dati in tabelle con righe e colonne, seguendo uno **schema rigido**. Utilizzano **[SQL](https://www.google.com/search?q=sql+database)** per gestire dati strutturati e relazionali, ideali per applicazioni aziendali, gestione di inventari e dati finanziari.
##### Non relazionali
I database NoSQL sono progettati per **memorizzare dati in modo flessibile e scalabile**, senza uno schema rigido. Possono gestire dati **non strutturati** o semi-strutturati, seguendo vari modelli come *documenti, chiave-valore, grafo o colonne*. Spesso offrono scalabilità orizzontale su **[cluster](https://www.google.com/search?q=cluster+database)** e sono adatti per applicazioni con dati complessi, non strutturati o altamente distribuiti, come applicazioni Web, analisi dei big data e flussi di dati in tempo reale.

<br>

| Caratteristica                   | Database Relazionali    | Database Document-Oriented  |
|----------------------------------|-------------------------|-----------------------------|
| **Modello di Dati**                  | Tabellare con rigide relazioni tra le tabelle | Flessibile, basato su documenti con dati semi-strutturati |
| **Schema dei Dati**                 | Schema rigido, definito in anticipo | Schema dinamico, senza necessità di uno schema rigido |
| **Linguaggio di Query**            | SQL (Structured Query Language) | Query specifiche del database o linguaggi di query adatti |
| **Scalabilità**                      | Solitamente scalabilità verticale (aggiornare l'hardware) | Scalabilità orizzontale su cluster |
| **Consistenza dei Dati**             | Struttura transazionale con forte consistenza | Modello di consistenza eventuale |
| **Esempi Noti**                      | MySQL, PostgreSQL, Oracle, SQL Server | MongoDB, Couchbase, RavenDB |
| **Casi d'Uso Tipici**                | Applicazioni con schemi dati ben definiti e operazioni transazionali | Applicazioni con dati non strutturati o semi-strutturati, scalabilità e flessibilità di query |

<br>

### SQL
SQL (Structured Query Language) è un **linguaggio di programmazione** utilizzato per **comunicare** con i *sistemi di gestione dei database* (DBMS) al fine di creare, gestire e interrogare basi di dati relazionali. SQL è progettato per l'interazione con database relazionali, come [MySQL](https://www.mysql.com/), [PostgreSQL](https://www.postgresql.org/), [Oracle](https://www.oracle.com/), [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server) e molti altri. È un linguaggio standardizzato con una sintassi (non CASE SENSITIVE) chiara e regole ben definite.

Con SQL si possono fare seguenti operazioni:

* Creazione di tabelle (DDL)
* Inserimento di dati (DML)
* Aggiornamento dei dati (DML)
* Cancellazione dei dati (DML)
* Interrogazione dei dato (DML)
* Gestione dei permessi di accesso (DCL)

<br>

# Data Manipulation Language
La Data Manipulation Language (DML) è una parte del linguaggio SQL (Structured Query Language) utilizzata per manipolare i dati all'interno di un database relazionale. 

La DML consente di eseguire le seguenti azioni principali:

* Inserimento di dati (INSERT): La DML permette di aggiungere nuovi dati a una tabella esistente del database.
* Aggiornamento dei dati (UPDATE): È possibile utilizzare la DML per modificare o aggiornare dati esistenti all'interno di una tabella.
* Cancellazione dei dati (DELETE): La DML consente di rimuovere dati da una tabella, sia in base a condizioni specifiche che per eliminare tutti i dati.
* Interrogazione dei dati (SELECT)

[▴ top](#Contenuti)
<br>
<br>

## Selezione dei dati
### SELECT statement
#### Tutte colonne
Verranno mostrate tutte colonne di una specifica tabella
```sql
SELECT *
FROM nome_tabella;
```

#### Colonne specifiche
Verranno mostrate solo le colonne selezionate (colonna1 e colonna2)
```sql
SELECT 
	colonna1,
	colonna2
FROM nome_tabella;
```
#### Colonne con alias
Possiamo assegnare dei nomi più comprensibili utilizzando AS, in questo caso colonna1 verrà mostrata con il "Nome" e la colonna2 con il "Cognome"
```sql
SELECT 
	colonna1 AS Nome,
	colonna2 AS Cognome
FROM nome_tabella;
```
#### Colonne con espressioni aritmetiche
Possiamo mostrare delle colonne che effettuando dei calcoli aritmetici, molto utili poiché non ce bisogno di creare colonne inutili!
Espressioni supportate: + - / * %
```sql
SELECT 
	colonna1,
	(colonna2 * 2) AS 'Doppio valore' -- spazio? mettici le ' o "
FROM nome_tabella;
```
#### Seleziona dati univoci
Verranno ignorati i valori ripetuti
```sql
SELECT DISTINCT colonna1
FROM nome_tabella;
```

[▴ top](#Contenuti)
<br>
<br>

### Filtraggio dei dati
#### Corrispondenze parziali o pattern
Questa query seleziona i nomi dei clienti che iniziano con "Jo".
```sql
SELECT
	Nome
FROM Clienti
WHERE Nome LIKE 'Jo%';
```

Questa query selezionerà i nomi dei clienti che terminano con la sequenza "son".
```sql
SELECT
	Nome
FROM Clienti
WHERE Nome LIKE '%son';
```

Questa query selezionerà i titoli dei libri che contengono la parola "avventura" ovunque nel titolo.
```sql
SELECT
	Titolo
FROM Libri 
WHERE Titolo LIKE '%avventura%';
```

Questa query selezionerà le parole che hanno tre lettere, dove il carattere mancante può essere qualsiasi lettera. Ad esempio, potrebbe corrispondere a "cat", "cot", "cut", ecc.
```sql
SELECT
	Parola
FROM Dizionario
WHERE Parola LIKE 'c_t';
```
#### Valore specifico in una colonna
Questa query seleziona tutti gli ordini in cui il prodotto è specificamente "Computer".
```sql
SELECT
	Prodotto
FROM Ordini
WHERE Prodotto = 'Computer';
```
#### Valore NULL o non NULL
Questa query seleziona i nomi dei clienti che non hanno un indirizzo specificato, ovvero il valore della colonna "Indirizzo" è NULL.

L'operatore IS NULL viene utilizzato per verificare se un valore è nullo.
```sql
SELECT
	Nome
FROM Clienti
WHERE Indirizzo IS NULL;
```
Questa query selezionerà tutti i record dalla tabella "Prodotti" in cui il valore nella colonna "Descrizione" non è nullo. 
```sql
SELECT *
FROM Prodotti
WHERE Descrizione IS NOT NULL;
```
#### Filtrare utilizzando una lista dei valori
Questa query seleziona tutti gli ordini in cui il prodotto è uno dei valori elencati nella lista (Libro, Computer, Cuffie). 

L'operatore IN permette di filtrare i risultati in base a una lista di valori specifici.
```sql
SELECT
	Prodotto
FROM Ordini 
WHERE Prodotto IN ('Libro', 'Computer', 'Cuffie');
```

[▴ top](#Contenuti)
<br>
<br>