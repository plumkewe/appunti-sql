# 🍯 Appunti SQL

Il software che utilizziamo a scuola è:
<p>
<img height="32" width="32" src="https://cdn.simpleicons.org/xampp/orange" alt="XAMPP"/>
</p>

`ℹ️` [Scopri di più](https://en.wikipedia.org/wiki/XAMPP) `⭐️` [Esercizi svolti](https://github.com/plumkewe/scuola/tree/main/Attivita-svolta/2023/SQL) `🌎` [W3S](https://www.w3schools.com/sql/default.asp) 


> **Note**\
> Verrà aggiornato solo quando avrò voglia!

### Da fare
- [ ] Migliorare la sezione contenuti
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
	- [`CASE WHEN` più esplicito](#case-when-più-esplicito)
	- [Struttura più chiara](#struttura-più-chiara)
	- [Espressioni aritmetiche](#espressioni-aritmetiche)
	- [Alias significativi](#alias-significativi)
- [Data Manipulation Language (DML)](#data-manipulation-language-dml)
	- [Selezione dei dati](#selezione-dei-dati)
		- [SELECT statement](#select-statement)
			- [Tutte colonne](#tutte-colonne)
			- [Colonne specifiche](#colonne-specifiche)
			- [Colonne con alias](#colonne-con-alias-as)
			- [Colonne con espressioni aritmetiche](#colonne-con-espressioni-aritmetiche)
			- [Seleziona dati univoci](#seleziona-dati-univoci-distinct)
		- [Filtraggio dei dati](#filtraggio-dei-dati)
			- [Corrispondenze parziali o pattern](#corrispondenze-parziali-o-pattern-like)
			- [Valore specifico in una colonna](#valore-specifico-in-una-colonna)
			- [Valore NULL o non NULL](#valore-null-o-non-null-is-nullis-not-null)
			- [Filtrare utilizzando una lista dei valori](#filtrare-utilizzando-una-lista-dei-valori-in)
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
		- [Ordinamento dei risultati](#ordinamento-dei-risultati-order-by)
		- [Limitazione dei risultati](#limitazione-dei-risultati-limit)
	- [Operatori di aggregazione](#operatori-di-aggregazione)
		- [Sommare i valori](#sommare-i-valori-sum)
		- [Calcolare la media](#calcolare-la-media-avg)
		- [Contare](#contare-count)
		- [Valore massimo](#valore-massimo-max)
		- [Valore minimo](#valore-minimo-min)
		- [Arrotondamento](#arrotondamento-round)
	- [`JOIN` delle tabelle](#join-delle-tabelle)
		- [INNER JOIN](#inner-join)
		- [LEFT JOIN](#left-join)
		- [RIGHT JOIN](#right-join)
		- [FULL JOIN](#full-join)
- [Modifica dei dati](#modifica-dei-dati)
	- [INSERT INTO](#insert-into)
	- [UPDATE](#update)
	- [DELETE](#delete)
	- [Transazioni](#transazioni)
	
## Definizioni
### Database
Un database è un insieme organizzato di dati. Può essere tutto, da un semplice elenco di contatti telefonici fino a un intero inventario di prodotti per un'azienda.

#### DBMS
Un DBMS è un software che gestisce i database. Esempi comuni sono MySQL, PostgreSQL, MongoDB e SQLite.

#### Relazionali
UUn database relazionale è un tipo di database che organizza i dati in tabelle con righe e colonne, molto simile a come i dati sono organizzati in un foglio di calcolo. Ogni riga rappresenta un record distinto e ogni colonna rappresenta un campo di quel record. Le tabelle possono essere collegate tra loro attraverso chiavi primarie e chiavi esterne, permettendo di creare relazioni tra i dati. Questo modello di database è molto comune e largamente utilizzato in molte applicazioni. Esempi di DBMS relazionali includono MySQL, PostgreSQL e SQLite.

#### NoSQL
I database NoSQL, o "non solo SQL", sono un tipo di database che non seguono il modello relazionale standard. Sono progettati per essere altamente scalabili e per gestire grandi quantità di dati distribuiti su molteplici macchine. I database NoSQL non richiedono uno schema fisso, il che significa che i dati possono essere inseriti nel database senza dover prima definire la struttura della tabella. Questo li rende molto flessibili e adatti per lavorare con dati non strutturati o semi-strutturati. Esistono diversi tipi di database NoSQL, tra cui database di documenti (come MongoDB), database di chiave-valore (come Redis), database di colonne (come Cassandra) e database di grafi (come Neo4j).

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

<br>
<br>

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
<details>
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
</details>

#### OR
Questa query selezionerà i nomi dei clienti che appartengono alla categoria "VIP" o alla categoria "Nuovi Clienti". 

L'operatore OR consente di selezionare le righe che soddisfano almeno una delle condizioni.
```sql
SELECT
	Nome
FROM Clienti
WHERE Categoria = 'VIP' OR Categoria = 'Nuovi Clienti';
```
<details>
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
</details>

#### AND e OR
Questa query selezionerà i nomi dei prodotti che appartengono alle categorie "Elettronica" o "Informatica" e hanno un prezzo superiore a 500 unità monetarie. 

Le parentesi sono utilizzate per definire le priorità delle condizioni.
```sql
SELECT
	Nome
FROM Prodotti
WHERE (Categoria = 'Elettronica' OR Categoria = 'Informatica') AND Prezzo > 500;
```
<details>
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
</details>

#### NOT
Questa query selezionerà i titoli dei libri che non appartengono al genere "Fantascienza". 

L'operatore NOT nega una condizione, selezionando le righe che non la soddisfano.
```sql
SELECT
	Titolo
FROM Libri
WHERE NOT Genere = 'Fantascienza';
```
<details>
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
</details>

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
<details>
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
		<!-- Altri dati della tabella Clienti -->
		<!-- ... -->
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
		<!-- Altri 4 risultati della tabella Clienti -->
		<!-- ... -->
	</table>
</details>
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
<details>
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
</details>
#### Limitazione dei risultati con offset
Questa query restituirà i nomi e i cognomi dei dipendenti a partire dal sesto (offset di 5) fino al decimo (5 risultati successivi).

L'istruzione OFFSET specifica da quale posizione iniziare a restituire i risultati.
```sql
SELECT
	Nome,
	Cognome
FROM Dipendenti LIMIT 5 OFFSET 5;
```
<details>
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
</details>

#### Limitazione dei risultati con combinazione di offset e limit
Questa query restituirà i titoli dei libri a partire dal 21simo (offset di 20) fino al trentesimo (10 risultati successivi).

La combinazione di LIMIT e OFFSET consente di recuperare porzioni specifiche di dati.
```sql
SELECT
	Titolo
FROM Libri LIMIT 10 OFFSET 20;
```
<details>
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
</details>

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
The `Orders` table:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|
| 4       | 4          | 2022-02-10|

The `Customers` table:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |
| 4          | Bob          |

If you want to combine these two tables to get a list of orders with the customer's name, you can use an INNER JOIN. The SQL query would look like this:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

This will return a table that only includes orders for which a corresponding customer exists:

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| 4       | Bob          | 2022-02-10|

#### LEFT JOIN
The `Orders` table:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|
| 4       | 5          | 2022-02-10|

The `Customers` table:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |

If you want to combine these two tables to get a list of orders with the customer's name, you can use a LEFT JOIN. The SQL query would look like this:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
LEFT JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

This will return a table that includes all orders, but customer names will only appear for orders where a corresponding customer exists. If an order has a `CustomerID` that doesn't exist in the `Customers` table, the `CustomerName` for that order will be NULL.

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| 4       | NULL         | 2022-02-10|

#### RIGHT JOIN
The `Orders` table:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|

The `Customers` table:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |
| 4          | Bob          |

If you want to combine these two tables to get a list of customers with their orders, you can use a RIGHT JOIN. The SQL query would look like this:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
RIGHT JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

This will return a table that includes all customers, but orders will only appear for customers where a corresponding order exists. If a customer doesn't have any orders in the `Orders` table, the `OrderID` and `OrderDate` for that customer will be NULL.

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| NULL    | Bob          | NULL      |

#### FULL JOIN
The `Orders` table:

| OrderID | CustomerID | OrderDate |
|---------|------------|-----------|
| 1       | 3          | 2022-01-22|
| 2       | 1          | 2022-03-20|
| 3       | 2          | 2022-04-22|
| 4       | 5          | 2022-02-10|

The `Customers` table:

| CustomerID | CustomerName |
|------------|--------------|
| 1          | John Doe     |
| 2          | Jane Doe     |
| 3          | Alice        |
| 4          | Bob          |

If you want to combine these two tables to get a list of all orders and all customers, you can use a FULL JOIN. The SQL query would look like this:

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
FULL JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

This will return a table that includes all orders and all customers. If an order has a `CustomerID` that doesn't exist in the `Customers` table, the `CustomerName` for that order will be NULL. Similarly, if a customer doesn't have any orders in the `Orders` table, the `OrderID` and `OrderDate` for that customer will be NULL.

| OrderID | CustomerName | OrderDate |
|---------|--------------|-----------|
| 1       | Alice        | 2022-01-22|
| 2       | John Doe     | 2022-03-20|
| 3       | Jane Doe     | 2022-04-22|
| 4       | NULL         | 2022-02-10|
| NULL    | Bob          | NULL      |

[`🔼`](#Contenuti)
<br>
<br>

<hr>
fatto da me e GitHub Copilot.