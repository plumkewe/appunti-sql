# 🍯 Appunti SQL

Il software che utilizziamo a scuola è:
<p>
<img height="32" width="32" src="https://cdn.simpleicons.org/xampp/orange" alt="XAMPP"/>
</p>

[Scopri di più](https://en.wikipedia.org/wiki/XAMPP) `⭐️` [Esercizi svolti](https://github.com/plumkewe/scuola/tree/main/Attivita-svolta/2023/SQL)


> **Note**\
> Verrà aggiornato solo quando avrò voglia!

### Da fare
- [ ] Migliorare la sezione contenuti
- [ ] Migliorare la dimostrazione

<br>

## Contenuti
<!--   -->
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
<!--   -->
### [Consigli](#Consigli)
* [`CASE WHEN` più esplicito](#CASE-WHEN-più-esplicito)
* [Struttura più chiara](#Struttura-più-chiara)
* [Espressioni aritmetiche](#Espressioni-aritmetiche)
* [Alias significativi](#Alias-significativi)
<!--   -->
### [Data Manipulation Language](#Data-Manipulation-Language) (DML)
* [Selezione dei dati](#Selezione-dei-dati)
	* [SELECT statement](#SELECT-statement)
		* [Tutte colonne](#Tutte-colonne)
		* [Colonne specifiche](#Colonne-specifiche)
		* [Colonne con alias](#Colonne-con-alias) `AS`
		* [Colonne con espressioni aritmetiche](#Colonne-con-espressioni-aritmetiche)
		* [Seleziona dati univoci](#Seleziona-dati-univoci) `DISTINCT`
	* [Filtraggio dei dati](#Filtraggio-dei-dati)
		* [Corrispondenze parziali o pattern](#Corrispondenze-parziali-o-pattern) `LIKE`
		* [Valore specifico in una colonna](#Valore-specifico-in-una-colonna)
		* [Valore NULL o non NULL](#Valore-NULL-o-non-NULL) `IS NULL`/`IS NOT NULL`
		* [Filtrare utilizzando una lista dei valori](#Filtrare-utilizzando-una-lista-dei-valori) `IN`
	* [Operatori di confronto](#Operatori-di-confronto)
		* [Ugualianza](#Ugualianza) `=`
		* [Disugualianza](#Disugualianza) `<>` o `!=`
		* [Maggiore di](#Maggiore-di) `>`
		* [Maggiore o uguale di](#Maggiore-o-uguale-di]) `>=`
		* [Minore](#Minore) `<`
		* [Minore o uguale di](#Minore-o-uguale-di) `=<`
	* [Operatori logici](Operatori-logici)
		* [AND](#AND)
		* [OR](#OR)
		* [AND e OR](#AND-e-OR)
		* [NOT](#NOT)
			* Negare condizioni multiple
	* [Ordinamento dei risultati](#Ordinamento-dei-risultati) `ORDER BY`
		* [Ordinamento crescente per una colonna](#Ordinamento-crescente-per-una-colonna) `ASC`
		* [Ordinamento decrescente per una colonna](#Ordinamento-decrescente-per-una-colonna) `DESC`
		* [Ordinamento per più colonne](#Ordinamento-per-più-colonne)
		* [Ordinamento con espressioni aritmetiche](#Ordinamento-con-espressioni-aritmetiche)
	* [Limitazione dei risultati](#Limitazione-dei-risultati) `LIMIT`
		* [Limitazione del numero di righe restituite](#Limitazione-del-numero-di-righe-restituite)
		* [Limitazione dei risultati con ordinamento](#Limitazione-dei-risultati-con-ordinamento)
		* [Limitazione dei risultati con offset](#Limitazione-dei-risultati-con-offset)
		* [Limitazione dei risultati con combinazione di offset e limit](#Limitazione-dei-risultati-con-combinazione-di-offset-e-limit)
* [Operatori di aggregazione](#Operatori-di-aggregazione)
	* [Sommare i valori](#Sommare-i-valori) `SUM`
		* [Sommare i valori per ciascun gruppo](#Sommare-i-valori-per-ciascun-gruppo) `SUM` con `GROUP BY`
	* [Calcolare la media](#Calcolare-la-media) `AVG`
		* [Calcolare la media condizionale](#Calcolare-la-media-condizionale) `AVG` con `CASE WHEN`
		* [Calcolare la media ponderata](#Calcolare-la-media-ponderata) `SUM` e `AVG` con espressioni aritmetiche
	* [Contare](#Contare) `COUNT`
		* [Contare valori distinti](#Contare-valori-distinti) `COUNT` con `DISTINCT`
	* [Valore massimo](#Valore-massimo) `MAX`
		* [Valore massimo per ciascun gruppo](#Valore-massimo-per-ciascun-gruppo) `MAX` con `GROUP BY`
	* [Valore minimo](#Valore-minimo) `MIN`
		* [Valore minimo condizionale](#Valore-minimo-condizionale) `MIN` con `CASE WHEN`
	* [Arrotondamento](#Arrotondamento) `ROUND`
* `JOIN` delle tabelle
	* INNER JOIN
	* LEFT JOIN
	* RIGHT JOIN
* Modifica dei dati
	* INSERT INTO
	* UPDATE
	* DELETE
	* Transazioni
		* BEGIN
		* COMMIT
		* ROLLBACK
<!--   -->
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
La Data Manipulation Language (DML) è una parte del linguaggio SQL (Structured Query Language) utilizzata per manipolare i dati all'interno di un database relazionale. 

La DML consente di eseguire le seguenti azioni principali:

* Inserimento di dati (INSERT): La DML permette di aggiungere nuovi dati a una tabella esistente del database.
* Aggiornamento dei dati (UPDATE): È possibile utilizzare la DML per modificare o aggiornare dati esistenti all'interno di una tabella.
* Cancellazione dei dati (DELETE): La DML consente di rimuovere dati da una tabella, sia in base a condizioni specifiche che per eliminare tutti i dati.
* Interrogazione dei dati (SELECT)

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

<hr>
fatto da me.