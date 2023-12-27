# 🍯 Appunti SQL

Il software che utilizziamo a scuola è:
<p>
<img height="32" width="32" src="https://cdn.simpleicons.org/xampp/orange" alt="XAMPP"/>
</p>

`ℹ️` [Scopri di più](https://en.wikipedia.org/wiki/XAMPP) `⭐️` [Esercizi svolti](https://github.com/plumkewe/scuola/tree/main/Attivita-svolta/2023/SQL) `🌎` [W3S](https://www.w3schools.com/sql/default.asp) `👩‍🏫` [Presentazioni](/presentazione)


> **Note**\
> Verrà aggiornato solo quando avrò voglia!

### Da fare
- [x] ~Migliorare la sezione contenuti~
- [x] ~Tradurre le spiegazini~
- [x] ~Evidenziare parole importanti nel testo~
- [ ] Migliorare la dimostrazione

<br>

## Contenuti
- [Definizioni](#definizioni)
	- [Database](#database)
		- [DBMS](#dbms)
		- [Relazionali](#relazionali)
		- [NoSQL](#nosql)
	- [SQL](#sql)
		- [Query](#query)
			- [Query clauses](#query-clauses)
		- [Primary key](#primary-key)
		- [Foreign key](#foreign-key)
		- [DDL](#DDL)
		- [DML](#DML)
		- [DCL](#DCL)
- [Consigli](#consigli)
	- [CASE WHEN più esplicito](#case-when-più-esplicito)
	- [Struttura più chiara](#struttura-più-chiara)
	- [Espressioni aritmetiche](#espressioni-aritmetiche)
	- [Alias significativi](#alias-significativi)
- [Data Manipulation Language (DML)](#data-manipulation-language)
	- [Selezione dei dati](#selezione-dei-dati)
		- [SELECT statement](#select-statement)
			- [Tutte colonne](#tutte-colonne)
			- [Colonne specifiche](#colonne-specifiche)
			- [Colonne con alias](#colonne-con-alias)
			- [Colonne con espressioni aritmetiche](#colonne-con-espressioni-aritmetiche)
			- [Seleziona dati univoci](#seleziona-dati-univoci)
		- [Filtraggio dei dati](#filtraggio-dei-dati)
			- [Corrispondenze parziali o pattern](#corrispondenze-parziali-o-pattern)
			- [Valore specifico in una colonna](#valore-specifico-in-una-colonna)
			- [Valore NULL o non NULL](#valore-null-o-non-null)
			- [Filtrare utilizzando una lista dei valori](#filtrare-utilizzando-una-lista-dei-valori)
		- [Operatori di confronto](#operatori-di-confronto)
			- [Ugualianza](#ugualianza)
			- [Disugualianza](#disugualianza)
			- [Maggiore di](#maggiore-di)
			- [Maggiore o uguale di](#maggiore-o-uguale-di)
			- [Minore](#minore)
			- [Minore o uguale di](#minore-o-uguale-di)
		- [Operatori logici](#operatori-logici)
			- [AND](#and)
			- [OR](#or)
			- [AND e OR](#and-e-or)
			- [NOT](#not)
		- [Ordinamento dei risultati](#ordinamento-dei-risultati)
		- [Limitazione dei risultati](#limitazione-dei-risultati)
	- [Operatori di aggregazione](#operatori-di-aggregazione)
		- [Sommare i valori](#sommare-i-valori)
		- [Calcolare la media](#calcolare-la-media)
		- [Contare](#contare)
		- [Valore massimo](#valore-massimo)
		- [Valore minimo](#valore-minimo)
		- [Arrotondamento](#arrotondamento)
	- [JOIN delle tabelle](#join)
		- [INNER JOIN](#inner-join)
		- [LEFT JOIN](#left-join)
		- [RIGHT JOIN](#right-join)
		- [FULL JOIN](#full-join)
		- [Unione implicita](#unione-implicita)
	- [Subquery](#Subquery)
		- [Che restituiscono un valore](#Che-restituiscono-un-valore)
			- [MAX](#MAX)
			- [AVG](#AVG)
		- [Subquery che restituiscono più valori](#Subquery-che-restituiscono-più-valori)
			- [IN](#IN)
			- [NOT IN](#NOT-IN)
			- [ANY](#ANY)
			- [ALL](#ALL)
			- [EXISTS](#EXISTS)
			- [NOT EXISTS](#NOT-EXISTS)
		- [Query correlate](#Query-correlate)
		- [Subquery nella FROM](#Subquery-nella-FROM)
		
<!-- - [Modifica dei dati](#modifica-dei-dati)
	- [INSERT INTO](#insert-into)
	- [UPDATE](#update)
	- [DELETE](#delete)
	- [Transazioni](#transazioni) -->
	
## Definizioni
### Database
Un database è un insieme organizzato di dati. Può essere tutto, da un semplice elenco di contatti telefonici fino a un intero inventario di prodotti per un'azienda.

#### DBMS
Un DBMS è un software che gestisce i database. Esempi comuni sono MySQL, PostgreSQL, MongoDB e SQLite.

#### Relazionali
Un database relazionale è un tipo di database che organizza i dati in **tabelle** con **righe** e **colonne**, molto simile a come i dati sono organizzati in un **foglio di calcolo**. Ogni **riga** rappresenta un **record** distinto e ogni **colonna** rappresenta un **campo** di quel **record**. Le **tabelle** possono essere collegate tra loro attraverso **chiavi primarie** e **chiavi esterne**, permettendo di creare **relazioni** tra i dati. Questo modello di database è molto comune e largamente utilizzato in molte applicazioni. Esempi di **DBMS relazionali** includono **MySQL**, **PostgreSQL** e **SQLite**.

#### NoSQL
I **database NoSQL**, o "non solo SQL", sono un tipo di database che non seguono il **modello relazionale** standard. Sono progettati per essere **altamente scalabili** e per gestire **grandi quantità di dati distribuiti** su molteplici macchine. I **database NoSQL** non richiedono uno **schema fisso**, il che significa che i dati possono essere inseriti nel database senza dover prima definire la **struttura della tabella**. Questo li rende molto **flessibili** e adatti per lavorare con **dati non strutturati** o **semi-strutturati**. Esistono diversi tipi di **database NoSQL**, tra cui **database di documenti** (come **MongoDB**), **database di chiave-valore** (come **Redis**), **database di colonne** (come **Cassandra**) e **database di grafi** (come **Neo4j**)..

#### DDL
Comandi utilizzati per definire o modificare la struttura di un database o di una tabella. Esempi di comandi DDL includono `CREATE`, `ALTER` e `DROP`.

#### DML
Comandi utilizzati per manipolare i dati all'interno delle tabelle di un database. Esempi di comandi DML includono `SELECT`, `INSERT`, `UPDATE` e `DELETE`.

#### DCL
Comandi utilizzati per controllare l'accesso ai dati all'interno del database. Esempi di comandi DCL includono `GRANT` e `REVOKE`, che sono utilizzati per gestire i diritti e i privilegi degli utenti.

<br>

### SQL
SQL è un linguaggio di programmazione utilizzato per comunicare con e manipolare i database.

Con SQL si possono fare seguenti operazioni:
<table>
<tbody>
  <tr>
    <td><b>DDL</b></td>
    <td>Creazione di tabelle</td>
  </tr>
  <tr>
    <td rowspan="3"><b>DML</b></td>
    <td>Aggiornamento dei dati</td>
  </tr>
  <tr>
    <td>Cancellazione dei dati</td>
  </tr>
  <tr>
    <td>Interrogazione dei dati</td>
  </tr>
  <tr>
    <td><b>DCL</b></td>
    <td>Gestione dei permessi di accesso</td>
  </tr>
</tbody>
</table>

#### Query
Una query SQL è un modo di comunicare con il **database** per ottenere le **informazioni** di cui hai bisogno o per effettuare ****modifiche** nei dati. Detto meglio: Una query è una richiesta di dati da un database.
##### Query clauses
<table>
	<tbody>
		<tr>
			<td><code>select</code></td>
			<td>Determines which columns to include in the query's result set</td>
		</tr>
		<tr>
			<td><code>from</code></td>
			<td>Identifies the tables from which to retrive data and how the tables should be joined</td>
		</tr>
		<tr>
			<td><code>where</code></td>
			<td>Filters out unwanted data</td>
		</tr>
		<tr>
			<td><code>group by</code></td>
			<td>Used to group rows together by common column values</td>
		</tr>
		<tr>
			<td><code>having</code></td>
			<td>Filters out unwanted groups</td>
		</tr>
		<tr>
			<td><code>order by</code></td>
			<td>Sorts the rows of the final result set by one or more columns</td>
		</tr>
	</tbody>
</table>

#### Primary key
Una chiave primaria è un campo unico in una tabella che può identificare ogni riga.

#### Foreign key
Una chiave esterna è un campo in una tabella che fa riferimento alla chiave primaria di un'altra tabella.

<br>
<br>

## Consigli
### CASE WHEN più esplicito
Rendi il blocco CASE WHEN più esplicito, elencando tutte le condizioni in modo chiaro.
```sql
SELECT
	Nome,
	CASE
		WHEN Età < 18 THEN 'Minorenne'
		WHEN Età >= 18 AND Età < 65 THEN 'Adulto'
		ELSE 'Anziano'
	END AS FasciaEtà
FROM
	Persone;
```
### Struttura più chiara
Indenta il codice in modo che le clausole siano chiaramente visibili e allinea i termini per una migliore leggibilità.
```sql
SELECT
	Colonna1,
	Colonna2
FROM
	Tabella
WHERE
	Condizione = 'Valore';
```
### Espressioni aritmetiche
Evita ambiguità nelle operazioni aritmetiche utilizzando le parentesi per definire la precedenza degli operatori.
```sql
SELECT 
	(Colonna1 + Colonna2) * Colonna3 AS Risultato
FROM
	Tabella;
```
### Alias significativi
Usa alias significativi per rendere chiare le colonne calcolate.
```sql
SELECT
	Nome,
	(Punteggio1 + Punteggio2) / 2 AS MediaPunteggio
FROM
	Studenti;
```

<br>
<br>

# Data Manipulation Language
La **Data Manipulation Language (DML)** è una parte del linguaggio SQL (*Structured Query Language*) utilizzata per manipolare i dati all'interno di un database relazionale.

La **DML** consente di eseguire le seguenti azioni principali:

* *Inserimento di dati (INSERT)*: La DML permette di aggiungere nuovi dati a una tabella esistente del database.
* *Aggiornamento dei dati (UPDATE)*: È possibile utilizzare la DML per modificare o aggiornare dati esistenti all'interno di una tabella.
* *Cancellazione dei dati (DELETE)*: La DML consente di rimuovere dati da una tabella, sia in base a condizioni specifiche che per eliminare tutti i dati.
* *Interrogazione dei dati (SELECT)*

## Selezione dei dati
### SELECT statement
#### Tutte colonne
Verranno mostrate **tutte colonne** di una specifica tabella
```sql
SELECT *
FROM nome_tabella;
```

#### Colonne specifiche
Verranno mostrate solo le **colonne selezionate** (colonna1 e colonna2)
```sql
SELECT 
	colonna1,
	colonna2
FROM nome_tabella;
```
#### Colonne con alias
Possiamo assegnare dei nomi più comprensibili utilizzando **AS**, in questo caso colonna1 verrà mostrata con il "Nome" e la colonna2 con il "Cognome"
> **Note**\
> Si può anche omettere il AS, funzionerà ugualmente

```sql
SELECT
	colonna1 AS Nome,
	colonna2 AS Cognome
FROM nome_tabella;
```

In questa query:
* `Orders AS o` assegna l'alias `o` alla tabella `Orders`
* `Customers AS c` assegna l'alias `c` alla tabella `Customers`
* `Products AS p` assegna l'alias `p` alla tabella `Products`

```sql
SELECT
	o.OrderID,
	c.CustomerName,
	p.ProductName,
	o.Quantity
FROM
	Orders AS o
INNER JOIN
	Customers AS c ON o.CustomerID = c.CustomerID
INNER JOIN
	Products AS p ON o.ProductID = p.ProductID;
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

[`🔼`](#Contenuti)
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

[`🔼`](#Contenuti)
<br>
<br>

### Operatori di confronto
#### Ugualianza
Questa query selezionerà i nomi dei clienti che hanno la città di residenza uguale a "Roma". 

L'operatore = viene utilizzato per confrontare i valori in modo esatto.
```sql
SELECT
	Nome
FROM Clienti
WHERE Città = 'Roma';
```
#### Disugualianza
Questa query selezionerà i prodotti nel magazzino che hanno una quantità diversa da zero. 

Gli operatori <> o != indicano che il valore nella colonna "Quantità" è diverso da zero.
```sql
SELECT
	Prodotto
FROM Magazzino 
WHERE Quantità <> 0;
```
#### Maggiore di
Questa query selezionerà i nomi e le età degli studenti che hanno un'età superiore a 18 anni. 

L'operatore > indica che il valore nella colonna "Età" deve essere maggiore di 18.
```sql
SELECT
	Nome,
	Età
FROM Studenti
WHERE Età > 18;
```
#### Maggiore o uguale di
Questa query selezionerà i nomi degli studenti e i voti degli esami in cui il voto è uguale o maggiore di 60. 

L'operatore >= indica che il valore nella colonna "Voto" deve essere 60 o superiore.
```sql
SELECT
	Nome,
	Voto
FROM Esami
WHERE Voto >= 60;
```
#### Minore
Questa query selezionerà i nomi dei dipendenti con uno stipendio inferiore a 30.000 unità monetarie. 

L'operatore < indica che il valore nella colonna "Stipendio" deve essere inferiore a 30.000.
```sql
SELECT
	Nome
FROM Dipendenti
WHERE Stipendio < 30000;
```
#### Minore o uguale di
Questa query selezionerà i nomi degli atleti e i punteggi in cui il punteggio è uguale o inferiore a 100. 

L'operatore <= indica che il valore nella colonna "Punteggio" deve essere 100 o inferiore.
```sql
SELECT
	Nome,
	Punteggio
FROM Atleti
WHERE Punteggio <= 100;
```

[`🔼`](#Contenuti)
<br>
<br>

### Operatori logici
#### AND
Questa query selezionerà i nomi dei dipendenti che lavorano nel reparto "Vendite" e hanno uno stipendio superiore a 30.000 unità monetarie.

L'operatore AND combina due condizioni e richiede che entrambe siano vere per selezionare una riga.
```sql
SELECT
	Nome
FROM Dipendenti 
WHERE Reparto = 'Vendite' AND Stipendio > 30000;
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Nome</th>
			<th>Reparto</th>
			<th>Stipendio</th>
		</tr>
		<tr>
			<td>Mario</td>
			<td>Vendite</td>
			<td>35000</td>
		</tr>
		<tr>
			<td>Laura</td>
			<td>Vendite</td>
			<td>28000</td>
		</tr>
		<tr>
			<td>Luigi</td>
			<td>Logistica</td>
			<td>32000</td>
		</tr>
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Nome</th>
		</tr>
		<tr>
			<td>Mario</td>
		</tr>
	</table>
</details> -->

#### OR
Questa query selezionerà i nomi dei clienti che appartengono alla categoria "VIP" o alla categoria "Nuovi Clienti". 

L'operatore OR consente di selezionare le righe che soddisfano almeno una delle condizioni.
```sql
SELECT
	Nome
FROM Clienti
WHERE Categoria = 'VIP' OR Categoria = 'Nuovi Clienti';
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Nome</th>
			<th>Categoria</th>
		</tr>
		<tr>
			<td>Anna</td>
			<td>VIP</td>
		</tr>
		<tr>
			<td>Giovanni</td>
			<td>Standard</td>
		</tr>
		<tr>
			<td>Luca</td>
			<td>Nuovi Clienti</td>
		</tr>
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Nome</th>
		</tr>
		<tr>
			<td>Anna</td>
		</tr>
		<tr>
			<td>Luca</td>
		</tr>
	</table>
</details> -->

#### AND e OR
Questa query selezionerà i nomi dei prodotti che appartengono alle categorie "Elettronica" o "Informatica" e hanno un prezzo superiore a 500 unità monetarie. 

Le parentesi sono utilizzate per definire le priorità delle condizioni.
```sql
SELECT
	Nome
FROM Prodotti
WHERE (Categoria = 'Elettronica' OR Categoria = 'Informatica') AND Prezzo > 500;
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Nome</th>
			<th>Categoria</th>
			<th>Prezzo</th>
		</tr>
		<tr>
			<td>Prodotto A</td>
			<td>Elettronica</td>
			<td>550</td>
		</tr>
		<tr>
			<td>Prodotto B</td>
			<td>Informatica</td>
			<td>450</td>
		</tr>
		<tr>
			<td>Prodotto C</td>
			<td>Elettronica</td>
			<td>480</td>
		</tr>
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Nome</th>
		</tr>
		<tr>
			<td>Prodotto A</td>
		</tr>
	</table>	
</details> -->

#### NOT
Questa query selezionerà i titoli dei libri che non appartengono al genere "Fantascienza". 

L'operatore NOT nega una condizione, selezionando le righe che non la soddisfano.
```sql
SELECT
	Titolo
FROM Libri
WHERE NOT Genere = 'Fantascienza';
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Titolo</th>
			<th>Genere</th>
		</tr>
		<tr>
			<td>Libro 1</td>
			<td>Fantascienza</td>
		</tr>
		<tr>
			<td>Libro 2</td>
			<td>Fantasy</td>
		</tr>
		<tr>
			<td>Libro 3</td>
			<td>Romanzo</td>
		</tr>
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Titolo</th>
		</tr>
		<tr>
			<td>Libro 2</td>
		</tr>
		<tr>
			<td>Libro 3</td>
		</tr>
	</table>
</details> -->

[`🔼`](#Contenuti)
<br>
<br>

### Ordinamento dei risultati
#### Ordinamento crescente per una colonna
Questa query selezionerà i nomi e le età degli studenti e li ordinerà in modo crescente in base all'età.

Il risultato mostrerà gli studenti dall'età più bassa alla più alta.

> **Note**\
> Se non specifici alcun tipo di ordinamento (né ASC né DESC), l'ordinamento di base sarà in modo ascendente (ASC).
```sql
SELECT
	Nome,
	Età
FROM Studenti
ORDER BY Età;
```
#### Ordinamento decrescente per una colonna
Questa query selezionerà i prodotti e i loro prezzi e li ordinerà in modo decrescente in base al prezzo.

Il risultato mostrerà i prodotti con il prezzo più alto prima.
```sql
SELECT
	Prodotto,
	Prezzo
FROM Prodotti
ORDER BY Prezzo DESC;
```
#### Ordinamento per più colonne
Questa query selezionerà i nomi, i cognomi e i punteggi degli studenti e li ordinerà in modo decrescente in base al punteggio e poi in modo crescente in base al cognome. 

> **Note**\
> Gli studenti con punteggi più alti verranno mostrati per primi, e in caso di punteggi uguali, verranno ordinati in base al cognome in ordine alfabetico crescente.
```sql
SELECT
	Nome,
	Cognome,
	Punteggio
FROM Studenti
ORDER BY Punteggio DESC, Cognome ASC;
```
#### Ordinamento con espressioni aritmetiche
Questa query selezionerà i nomi e gli stipendi annuali calcolati moltiplicando lo stipendio mensile per 12.

I risultati verranno ordinati in modo decrescente in base allo stipendio annuale.
```sql
SELECT
	Nome,
	Stipendio * 12 AS StipendioAnnuale
FROM Dipendenti
ORDER BY StipendioAnnuale DESC;
```
[`🔼`](#Contenuti)
<br>
<br>

### Limitazione dei risultati
#### Limitazione del numero di righe restituite
Questa query restituirà i nomi e i cognomi dei primi 5 clienti nella tabella "Clienti".

La clausola LIMIT viene utilizzata per limitare il numero di righe restituite ai primi 5 risultati.
```sql
SELECT
	Nome,
	Cognome
FROM Clienti LIMIT 5;
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Nome</th>
			<th>Cognome</th>
		</tr>
		<tr>
			<td>John</td>
			<td>Doe</td>
		</tr>
		
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Nome</th>
			<th>Cognome</th>
		</tr>
		<tr>
			<td>John</td>
			<td>Doe</td>
		</tr>
		
	</table> 
</details> -->

#### Limitazione dei risultati con ordinamento
Questa query selezionerà i nomi e i prezzi dei primi 3 prodotti ordinati in modo decrescente in base al prezzo.

La combinazione di ORDER BY e LIMIT consente di ottenere i primi N risultati dell'ordinamento desiderato.
```sql
SELECT
	Prodotto,
	Prezzo
FROM Prodotti
ORDER BY Prezzo DESC LIMIT 3;
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Prodotto</th>
			<th>Prezzo</th>
		</tr>
		<tr>
			<td>Prodotto A</td>
			<td>100</td>
		</tr>
		<i> Altri dati della tabella Prodotti ordinati per Prezzo </i>
		<i> ... </i>
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Prodotto</th>
			<th>Prezzo</th>
		</tr>
		<tr>
			<td>Prodotto C</td>
			<td>80</td>
		</tr>
		<i> Altri 2 risultati della tabella Prodotti ordinati per Prezzo </i>
		<i> ... </i>
	</table>
</details> -->

#### Limitazione dei risultati con offset
Questa query restituirà i nomi e i cognomi dei dipendenti a partire dal sesto (offset di 5) fino al decimo (5 risultati successivi).

L'istruzione OFFSET specifica da quale posizione iniziare a restituire i risultati.
```sql
SELECT
	Nome,
	Cognome
FROM Dipendenti LIMIT 5 OFFSET 5;
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Nome</th>
			<th>Cognome</th>
		</tr>
		<i> Dati della tabella Dipendenti </i>
		<i> ... </i>
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Nome</th>
			<th>Cognome</th>
		</tr>
		<tr>
			<td>Emily</td>
			<td>Johnson</td>
		</tr>
		<i> Altri 4 risultati della tabella Dipendenti (dal sesto al decimo) </i>
		<i> ... </i>
	</table>
</details>  -->

#### Limitazione dei risultati con combinazione di offset e limit
Questa query restituirà i titoli dei libri a partire dal 21simo (offset di 20) fino al trentesimo (10 risultati successivi).

La combinazione di LIMIT e OFFSET consente di recuperare porzioni specifiche di dati.
```sql
SELECT
	Titolo
FROM Libri LIMIT 10 OFFSET 20;
```
<!-- <details>
	<summary><b>Demostrazione</b></summary>
	<p>...</p>
	<table>
		<tr>
			<th>Titolo</th>
		</tr>
		<i>Dati della tabella Libri</i>
		<i> ... </i>
	</table>
	<p>Risultato:</p>
	<table>
		<tr>
			<th>Titolo</th>
		</tr>
		<tr>
			<td>Libro 21</td>
		</tr>
		<i> Altri 9 risultati della tabella Libri (dal ventunesimo al trentesimo) </i>
		<i> ... </i>
	</table>
</details> -->

[`🔼`](#Contenuti)
<br>
<br>

### Operatori di aggregazione
#### Sommare i valori
Questa query calcola la somma di tutti i valori nella colonna "Quantita" della tabella "Ordini" e restituisce il risultato con il nome "TotaleQuantita".
```sql
SELECT
	SUM(Quantita) AS TotaleQuantita
FROM Ordini;
```
##### Sommare i valori per ciascun gruppo
Questa query calcola la somma delle quantità di prodotti per ciascuna categoria nella tabella "Prodotti".
```sql
SELECT
	Categoria,
	SUM(Quantita) AS TotaleQuantita
FROM Prodotti
GROUP BY Categoria;
```
#### Calcolare la media
Questa query calcola la media dei valori nella colonna "Prezzo" della tabella "Prodotti" e restituisce il risultato con il nome "MediaPrezzo".
```sql
SELECT
	AVG(Prezzo) AS MediaPrezzo
FROM Prodotti;
```
##### Calcolare la media condizionale
Questa query calcola la media dei punteggi degli esami superiori a 70 per ciascun anno nella tabella "Esami".
```sql
SELECT
	Anno,
	AVG(CASE WHEN Punteggio > 70 THEN Punteggio ELSE NULL END) AS MediaSuperiori70
FROM Esami
GROUP BY Anno;
```
##### Calcolare la media ponderata
Questa query calcola la media ponderata dei punteggi degli studenti nella tabella "Voti", considerando il peso di ciascun voto.
```sql
SELECT
	Studente,
	AVG(Punteggio * Peso / 100) AS MediaPonderata
FROM Voti
GROUP BY Studente;
```
#### Contare
Questa query conta il numero totale di righe nella tabella "Clienti" e restituisce il risultato con il nome "NumeroClienti".
```sql
SELECT
	COUNT(*) AS NumeroClienti
FROM Clienti;
```
##### Contare valori distinti
Questa query conta il numero di categorie distinte nella tabella "Prodotti".
```sql
SELECT
	COUNT(DISTINCT Categoria) AS NumeroCategorie
FROM Prodotti;
```
#### Valore massimo
Questa query restituisce il valore massimo nella colonna "Punteggio" della tabella "Studenti" con il nome "PunteggioMassimo".
```sql
SELECT
	MAX(Punteggio) AS PunteggioMassimo
FROM Studenti;
```
##### Valore massimo per ciascun gruppo
Questa query restituisce il massimo stipendio per ciascun dipartimento nella tabella "Dipendenti".
```sql
SELECT
	Dipartimento,
	MAX(Stipendio) AS StipendioMassimo
FROM Dipendenti
GROUP BY Dipartimento;
```
#### Valore minimo
Questa query restituisce il valore minimo nella colonna "Quantita" della tabella "Magazzino" con il nome "QuantitaMinima".
```sql
SELECT
	MIN(Quantita) AS QuantitaMinima
FROM Magazzino;
```
##### Valore minimo condizionale
Questa query restituisce il voto minimo positivo per ciascun anno nella tabella "Esami".
```sql
SELECT Anno,
	MIN(CASE WHEN Voto > 0 THEN Voto ELSE NULL END) AS VotoMinimoPositivo
FROM Esami
GROUP BY Anno;
```
#### Arrotondamento
Questa query calcola la media dei voti nella colonna "MediaVoti" della tabella "Esami" e restituisce il risultato arrotondato a due decimali con il nome "MediaVotiArrotondata".
```sql
SELECT
	ROUND(MediaVoti, 2) AS MediaVotiArrotondata
FROM Esami;
```

[`🔼`](#Contenuti)
<br>
<br>

### Join
In SQL, un "JOIN" è un metodo per combinare righe provenienti da due o più tabelle, basato su una colonna correlata tra di loro. Ci sono diversi tipi di JOIN in SQL:

* **INNER JOIN**: Restituisce le righe quando c'è una corrispondenza in entrambe le tabelle.
* **LEFT JOIN**: Restituisce tutte le righe dalla tabella di sinistra, e le righe corrispondenti dalla tabella di destra. Se non c'è corrispondenza, il risultato è NULL sulla parte destra.
* **RIGHT JOIN**: Restituisce tutte le righe dalla tabella di destra, e le righe corrispondenti dalla tabella di sinistra. Se non c'è corrispondenza, il risultato è NULL sulla parte sinistra.
* **FULL JOIN**: Restituisce le righe quando c'è una corrispondenza in una delle tabelle. Quindi, se c'è una riga in una delle tabelle che non corrisponde con l'altra, il risultato sarà NULL.

#### INNER JOIN
La tabella `Orders`:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|
| 4       | 4          | 2022-02-10|

La tabella `Customers`:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |
| 4          | Bob          |

Se desideri combinare queste due tabelle per ottenere un elenco di ordini con il nome del cliente, puoi utilizzare un INNER JOIN. La query SQL sarebbe la seguente:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

Questa istruzione restituirà una tabella che include solo gli ordini per i quali esiste un cliente corrispondente:

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| 4       | Bob          | 2022-02-10|

#### LEFT JOIN
La tabella `Orders`:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|
| 4       | 5          | 2022-02-10|

La tabella `Customers`:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |

Se desideri combinare queste due tabelle per ottenere un elenco di ordini con il nome del cliente, puoi utilizzare un LEFT JOIN. La query SQL sarebbe la seguente:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
LEFT JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

Questa istruzione restituirà una tabella che include tutti gli ordini, ma i nomi dei clienti appariranno solo per gli ordini in cui esiste un cliente corrispondente. Se un ordine ha un `CustomerID` che non esiste nella tabella `Customers`, il `CustomerName` per quel determinato ordine sarà NULL.

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| 4       | NULL         | 2022-02-10|

#### RIGHT JOIN
La tabella `Orders`:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|

La tabella `Customers`:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |
| 4          | Bob          |

Se desideri combinare queste due tabelle per ottenere un elenco di clienti con i relativi ordini, puoi utilizzare un RIGHT JOIN. La query SQL sarebbe la seguente:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
RIGHT JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

Questa istruzione restituirà una tabella che include tutti i clienti, ma gli ordini appariranno solo per i clienti in cui esiste un ordine corrispondente. Se un cliente non ha nessun ordine nella tabella `Orders`, l'`OrderID` e l'`OrderDate` per quel cliente saranno NULL.

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| NULL    | Bob          | NULL      |

#### FULL JOIN
La tabella `Orders`:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|
| 4       | 5          | 2022-02-10|

La tabella `Customers`:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |
| 4          | Bob          |

Se vuoi combinare queste due tabelle per ottenere un elenco di tutti gli ordini e tutti i clienti, puoi utilizzare un FULL JOIN. La query SQL sarebbe la seguente:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
FULL JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

Questa istruzione restituirà una tabella che include tutti gli ordini e tutti i clienti. Se un ordine ha un `CustomerID` che non esiste nella tabella `Customers`, il `CustomerName` per quel determinato ordine sarà NULL. Allo stesso modo, se un cliente non ha nessun ordine nella tabella `Orders`, l'`OrderID` e l'`OrderDate` per quel cliente saranno NULL.

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| 4       | NULL         | 2022-02-10|
| NULL    | Bob          | NULL      |

### Unione implicita
<details>
  <summary><b>Spiegazione</b></summary>

  Questa query SQL seleziona dati da due tabelle: `Orders` e `Customers`. L'obiettivo è ottenere una lista di ordini insieme ai nomi dei clienti che hanno effettuato tali ordini.

  Ecco una spiegazione dettagliata di ciascuna parte della query:

  - `SELECT Orders.OrderID, Customers.CustomerName`: Questa parte della query specifica quali colonne di dati si desidera ottenere nel risultato. In questo caso, si desidera ottenere l'`OrderID` dalla tabella `Orders` e il `CustomerName` dalla tabella `Customers`.

  - `FROM Orders, Customers`: Questa parte della query specifica da quali tabelle si desidera ottenere i dati. In questo caso, si desidera ottenere i dati dalle tabelle `Orders` e `Customers`.

  - `WHERE Orders.CustomerID = Customers.CustomerID`: Questa è la clausola `WHERE` che stabilisce la condizione per unire le tabelle. In questo caso, le tabelle `Orders` e `Customers` vengono unite sulla base del `CustomerID`. Questo significa che per ogni riga nella tabella `Orders`, la query cerca una riga corrispondente nella tabella `Customers` dove `CustomerID` è lo stesso. In altre parole, per ogni ordine, la query trova il cliente che ha effettuato quell'ordine.

  Il risultato di questa query sarà un set di righe con `OrderID` e `CustomerName`, dove ogni riga rappresenta un ordine e il cliente che ha effettuato quell'ordine.
</details>

```sql
SELECT Orders.OrderID, Customers.CustomerName
FROM Orders, Customers
WHERE Orders.CustomerID = Customers.CustomerID;
```
[`🔼`](#Contenuti)
<br>
<br>

### Subquery
Una subquery, o sottoquery, è una query SQL che è **incorporata all'interno di un'altra query**. Una subquery può restituire dati a un comando SQL esterno, o può essere eseguita come un comando autonomo. Le subquery possono essere utilizzate in diverse istruzioni SQL come `SELECT`, `INSERT`, `UPDATE`, o `DELETE`.

#### Che restituiscono un valore
Una subquery che restituisce un valore è una subquery che restituisce un singolo valore. Questo tipo di subquery può essere utilizzato ovunque ci si aspetti un singolo valore, come in un'istruzione `SELECT`, `WHERE` o `HAVING`.

In questo esempio, la subquery `(SELECT AVG(punteggio) FROM studenti)` calcola il punteggio medio degli studenti. La query **esterna** poi seleziona i nomi e i punteggi degli studenti che hanno un punteggio superiore alla media.

```sql
SELECT nome, punteggio 
FROM studenti 
WHERE punteggio > (SELECT AVG(punteggio) FROM studenti);
```
<details>
  <summary><b>Spiegazione</b></summary>
	<ol>
		<li><p> La subquery <code>(SELECT AVG(punteggio) FROM studenti)</code> viene eseguita per prima. Questa subquery calcola il punteggio medio di tutti gli studenti nella tabella studenti.</p></li>
		<li><p> Il risultato della subquery (il punteggio medio) viene poi utilizzato nella clausola <code>WHERE</code> della query esterna.</p></li>
		<li><p>La query esterna <code>SELECT nome, punteggio FROM studenti WHERE punteggio > ...</code> viene quindi eseguita. Questa query seleziona le colonne  <code>nome</code> e <code>punteggio</code> dalla tabella <code>studenti</code>, ma solo per le righe in cui il <code>punteggio</code> è maggiore del punteggio medio calcolato dalla subquery.</p></li>	
	</ol>

</details>
##### MAX
La subquery `(SELECT MAX(punteggio) FROM studenti)` trova il punteggio più alto tra gli studenti. La query esterna poi seleziona i nomi e i punteggi degli studenti che hanno il punteggio massimo.

```sql
SELECT nome, punteggio 
FROM studenti 
WHERE punteggio > (SELECT AVG(punteggio) FROM studenti);
```
##### AVG
La subquery `(SELECT AVG(punteggio) FROM studenti)` calcola il punteggio medio degli studenti. La query esterna poi seleziona i nomi e i punteggi degli studenti che hanno un punteggio superiore alla media.

```sql
SELECT nome, punteggio 
FROM studenti 
WHERE punteggio = (SELECT MAX(punteggio) FROM studenti);
```
### Subquery che restituiscono più valori
Una subquery può restituire più valori, solitamente sotto forma di una colonna di valori. Questi valori possono poi essere utilizzati in combinazione con operatori come `IN`, `NOT IN`, `ANY`, `ALL`, `EXISTS`, `NOT EXISTS`.
#### IN
L'operatore `IN` verifica se un valore specifico corrisponde a qualsiasi valore all'interno di un elenco o restituito da una subquery.

la subquery restituisce un elenco di `id_studente` che hanno partecipato a un corso di matematica. La query esterna seleziona i nomi degli studenti che corrispondono a quegli ID. Quindi, otteniamo i nomi degli studenti che hanno partecipato al corso di matematica.

```sql
SELECT nome 
FROM studenti 
WHERE id IN (SELECT id_studente FROM corsi WHERE nome_corso = 'Matematica');
```

#### NOT IN
`NOT IN` è l'opposto di IN. Esclude invece di includere.

la subquery restituisce un elenco di `id_studente` che hanno partecipato a un corso di matematica. La query esterna seleziona i nomi degli studenti che non corrispondono a quegli ID, ovvero gli studenti che non hanno partecipato al corso di matematica.

```sql
SELECT nome 
FROM studenti 
WHERE id NOT IN (SELECT id_studente FROM corsi WHERE nome_corso = 'Matematica');
```
#### ANY
`ANY` viene utilizzato quando si desidera confrontare un valore con qualsiasi valore in un elenco di valori. 

la subquery restituisce un elenco di punteggi ottenuti in un esame di matematica. La query esterna seleziona i nomi degli studenti che hanno ottenuto un punteggio superiore a qualsiasi punteggio nell'elenco. Quindi, otteniamo i nomi degli studenti che hanno un punteggio superiore al punteggio più basso ottenuto nell'esame di matematica.

```sql
SELECT nome 
FROM studenti 
WHERE punteggio > ANY (SELECT punteggio FROM esami WHERE nome_esame = 'Matematica');
```
#### ALL
`ALL` è utilizzato quando si desidera confrontare un valore con tutti i valori in un elenco.

la subquery restituisce un elenco di punteggi ottenuti in un esame di matematica. La query esterna seleziona i nomi degli studenti che hanno ottenuto un punteggio superiore a tutti i punteggi nell'elenco. Quindi, otteniamo i nomi degli studenti che hanno un punteggio superiore al punteggio più alto ottenuto nell'esame di matematica.

```sql
SELECT nome 
FROM studenti 
WHERE punteggio > ALL (SELECT punteggio FROM esami WHERE nome_esame = 'Matematica');
```
#### EXISTS

`EXISTS` è utilizzato per verificare se esistono righe che soddisfano una determinata condizione.

la subquery verifica se esistono corsi a cui partecipa ciascuno studente. La query esterna seleziona i nomi degli studenti per i quali esiste almeno un corso. Quindi, otteniamo i nomi degli studenti che partecipano almeno a un corso.

```sql
SELECT nome 
FROM studenti 
WHERE EXISTS (SELECT * FROM corsi WHERE studenti.id = corsi.id_studente);
```
#### NOT EXISTS

`NOT EXISTS` è l'opposto di `EXISTS`. Viene utilizzato per verificare se non esistono righe che soddisfano una determinata condizione.

la subquery verifica se esistono corsi a cui partecipa ciascuno studente. La query esterna seleziona i nomi degli studenti per i quali non esiste alcun corso. Quindi, otteniamo i nomi degli studenti che non partecipano a nessun corso.

```sql
SELECT nome 
FROM studenti 
WHERE NOT EXISTS (SELECT * FROM corsi WHERE studenti.id = corsi.id_studente);
```
### Query correlate
Una query correlata, o subquery correlata, è una subquery che dipende dalla query esterna per i suoi valori. In altre parole, la subquery correlata utilizza i valori della query esterna. Questo significa che la subquery correlata viene eseguita una volta per ogni riga elaborata dalla query esterna.

In questo esempio, la query esterna seleziona i nomi degli impiegati dal database. La subquery correlata calcola la media dei salari per il dipartimento dell'impiegato corrente (come specificato dalla query esterna). La query esterna quindi confronta il salario dell'impiegato corrente con la media dei salari nel suo dipartimento, e se il salario dell'impiegato è superiore alla media, il nome dell'impiegato viene selezionato.

In questo caso, la subquery correlata viene eseguita una volta per ogni impiegato, perché il risultato della subquery correlata dipende dal dipartimento dell'impiegato corrente.

```sql
SELECT e1.nome 
FROM impiegati e1
WHERE salario > (
    SELECT AVG(salario)
    FROM impiegati e2
    WHERE e1.dipartimento = e2.dipartimento
);
```

<details>
  <summary><b>A cosa servono</b></summary>
	<p> Le query correlate in MySQL sono utilizzate per risolvere problemi che richiedono l'elaborazione di dati in modo sequenziale, piuttosto che in un unico set. Queste query sono utili quando il risultato di una query dipende dai risultati di altre query.
<br>
In termini semplici, una query correlata è come un ciclo in programmazione. Per ogni riga selezionata dalla query esterna, la subquery correlata viene eseguita una volta, utilizzando i valori di quella riga.
<br>
Ecco un esempio di utilizzo: supponiamo di avere un database di studenti e voti. Vuoi trovare tutti gli studenti che hanno un voto superiore alla media dei voti della loro classe. Una query correlata può aiutarti a risolvere questo problema. La query esterna andrebbe attraverso ogni studente, e per ogni studente, la subquery correlata calcolerebbe la media dei voti della sua classe e confronterebbe il voto dello studente con quella media.
<br>
Quindi, in sostanza, le query correlate sono utilizzate quando abbiamo bisogno di confrontare un valore con un gruppo di valori che cambia dinamicamente per ogni riga.
	</p>

<br>
<p>Supponiamo di avere la seguente tabella studenti: </p>

<table>
    <tr>
        <th>id</th>
        <th>nome</th>
        <th>classe</th>
        <th>voto</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Mario</td>
        <td>A</td>
        <td>85</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Luigi</td>
        <td>A</td>
        <td>90</td>
    </tr>
    <tr>
        <td>3</td>
        <td>Peach</td>
        <td>B</td>
        <td>95</td>
    </tr>
    <tr>
        <td>4</td>
        <td>Daisy</td>
        <td>B</td>
        <td>80</td>
    </tr>
    <tr>
        <td>5</td>
        <td>Bowser</td>
        <td>A</td>
        <td>70</td>
    </tr>
    <tr>
        <td>6</td>
        <td>Wario</td>
        <td>B</td>
        <td>85</td>
    </tr>
</table>

<p>Vogliamo trovare tutti gli studenti che hanno un voto superiore alla media dei voti della loro classe. La query correlata potrebbe essere la seguente:</p>

```sql
SELECT nome
FROM studenti s1
WHERE voto > (
    SELECT AVG(voto)
    FROM studenti s2
    WHERE s1.classe = s2.classe
);
```
<p>La query esterna scorre ogni studente. Per ogni studente, la subquery correlata calcola la media dei voti degli studenti nella stessa classe. Se il voto dello studente è superiore a questa media, il nome dello studente viene selezionato.</p> <br>

<p>Nel nostro esempio, la media dei voti per la classe A è (85 + 90 + 70) / 3 = 81.67 e per la classe B è (95 + 80 + 85) / 3 = 86.67. Quindi, la query restituirà Luigi (classe A, voto 90) e Peach (classe B, voto 95) poiché i loro voti sono superiori alla media dei voti delle rispettive classi.</p>


</details>
### Subquery nella FROM

Una subquery nella clausola `FROM` è utilizzata per creare una tabella temporanea che può essere utilizzata per l'elaborazione ulteriore nella query esterna. Questo è utile quando si desidera eseguire operazioni su un set di dati che è il risultato di un'altra query.

Ecco un esempio semplice:

Supponiamo di avere una tabella `vendite`:

| id_prodotto | quantita |
|-------------|----------|
| 1           | 10       |
| 2           | 20       |
| 3           | 30       |
| 1           | 40       |
| 2           | 50       |
| 3           | 60       |

E vuoi calcolare la quantità totale venduta per ogni prodotto. Potresti prima creare una tabella temporanea con la subquery nella clausola `FROM` che raggruppa le vendite per `id_prodotto` e calcola la somma della `quantita`. Quindi, nella query esterna, puoi selezionare da questa tabella temporanea.

```sql
SELECT id_prodotto, totale_quantita
FROM (
    SELECT id_prodotto, SUM(quantita) as totale_quantita
    FROM vendite
    GROUP BY id_prodotto
) AS vendite_aggregate;
```

La subquery nella clausola `FROM` crea una tabella temporanea `vendite_aggregate` che contiene l'`id_prodotto` e il `totale_quantita` per ogni prodotto. Quindi, la query esterna seleziona da questa tabella temporanea.

Il risultato sarebbe:

| id_prodotto | quantita |
|-------------|----------|
| 1           | 10       |
| 2           | 20       |
| 3           | 30       |
| 1           | 40       |
| 2           | 50       |
| 3           | 60       |


[`🔼`](#Contenuti)
<br>
<br>

<hr>
fatto da me, GitHub Copilot e ChatGPT.