# 🍯 Appunti SQL

> **Note**\
> Verrà aggiornato solo quando avrò voglia!

## Contenuti
* [Definizioni](#Definizioni)
	* [Database](#Database)
		* [DBMS](#DBMS)
		* [Tipi](#Tipi)
			* Relazionali
			* Non relazionali
	* [SQL](#SQL)
	* [DDL - Data Definition Language](#DDL)
	* [DML - Data Manipulation Language](#DML)
	* [DML - Data Control Language](#DML)
* [Data Manipulation Language (DML)](#Data-Manipulation-Language)
	* [Selezione dei dati](#Selezione-dei-dati)
		* [SELECT statement](#SELECT-statement)
			* [Tutte colonne](#Tutte-colonne)
			* [Colonne specifiche](#Colonne-specifiche)
			* [Colonne con alias (AS)](#Colonne-con-alias)
			* [Colonne con espressioni aritmetiche](#Colonne-con-espressioni-aritmetiche)
			* [Seleziona dati univoci (DISTINCT)](#Seleziona-dati-univoci)
		* Filtraggio dei dati (WHERE clause)
			* Corrispondenze parziali o pattern (LIKE)
			* Valore specifico in una colonna
			* Valore NULL o non NULL (IS NULL/IS NOT NULL)
			* Filtrare utilizzando una lista dei valori (IN)
		* Operatori di confronto (=, <, >, <=, >=, <>)
			* Ugualianza (=)
			* Disugualianza (<> o !=)
			* Maggiore di (>)
			* Maggiore o uguale di (>=)
			* Minore (<)
			* Minore o uguale di (=<)
		* Operatori logici (AND, OR, NOT)
			* AND
			* OR
			* AND e OR
			* NOT
				* Negare condizioni multiple
		* Ordinamento dei risultati (ORDER BY)
	
	
## Definizioni
### Database
#### DBMS
I Database Management System (DBMS) sono software progettati per gestire e organizzare dati in database. Esistono diversi tipi di DBMS, ognuno dei quali è progettato per scopi e casi d'uso specifici. Ecco alcuni dei tipi di DBMS più comuni:
DBMS Relazionale: Questo tipo di DBMS utilizza tabelle per memorizzare dati e gestisce relazioni tra tabelle. 
Esempi noti includono [MySQL](https://www.mysql.com/), [PostgreSQL](https://www.postgresql.org/), [Oracle database](https://www.oracle.com/), [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server).

![Esempio](https://static.packt-cdn.com/products/9781787129559/graphics/image_08_001.jpg)
#### Tipi
##### Relazionali
##### Non relazionali
### SQL
SQL (Structured Query Language) è un **linguaggio di programmazione** utilizzato per **comunicare** con i *sistemi di gestione dei database* (DBMS) al fine di creare, gestire e interrogare basi di dati relazionali. SQL è progettato per l'interazione con database relazionali, come [MySQL](https://www.mysql.com/), [PostgreSQL](https://www.postgresql.org/), [Oracle](https://www.oracle.com/), [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server) e molti altri. È un linguaggio standardizzato con una sintassi (non CASE SENSITIVE) chiara e regole ben definite.

Con SQL si possono fare seguenti operazioni:
* Creazione di tabelle (DDL)
* Inserimento di dati (DML)
* Aggiornamento dei dati (DML)
* Cancellazione dei dati (DML)
* Interrogazione dei dato (DML)
* Gestione dei permessi di accesso (DCL)
### DDL
### DML
### DCL

# Data Manipulation Language
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
