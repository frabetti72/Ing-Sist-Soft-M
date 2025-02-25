

## Analisi del problema
Qua di seguito l'analisi del problema

### Analisi delle funzionalità

#### Tabella funzionalità:

| Funzionalità                | Tipo                                                 | Grado complessità |
| --------------------------- | ---------------------------------------------------- | ----------------- |
| Start                       | interazione con l'esterno                            | semplice          |
| Stop                        | interazione con l'esterno                            | semplice          |
| Exit                        | interazione con l'esterno                            | semplice          |
| Stato iniziale              | interazione con l'esterno,<br>manipolazione dei dati | medio             |
| Rappresentazione visiva     | interazione con l'esterno                            | semplice          |
| comunicazione client-server | sincronizzazione                                     | medio             |
| realizzazione cella         | manipolazione dati                                   | semplice          |
#### Tabella informazioni/flusso:

##### Start:
| Informazione | Tipo     | Livello privacy | I/O            | Vincoli     |
| ------------ | -------- | --------------- | -------------- | ----------- |
| game on      | semplice | nessuno         | Input e Output | true, false |
##### Stop:
| Informazione | Tipo     | Livello privacy | I/O            | Vincoli     |
| ------------ | -------- | --------------- | -------------- | ----------- |
| game on      | semplice | nessuno         | Input e Output | true, false |
##### Exit: (none)

##### Stato iniziale:
| Informazione   | Tipo     | Livello privacy | I/O            | Vincoli            |
| -------------- | -------- | --------------- | -------------- | ------------------ |
| stato cella    | semplice | nessuno         | Input e Output | true, false        |
| stato iniziale | composto | nessuno         | Input          | stessa dim modello |
| stato corrente | composto | nessuno         | Output         | stessa dim modello |
##### Stato corrente:
| Informazione   | Tipo     | Livello privacy | I/O            | Vincoli            |
| -------------- | -------- | --------------- | -------------- | ------------------ |
| stato cella    | semplice | nessuno         | Input e Output | true, false        |
| stato iniziale | composto | nessuno         | Input          | stessa dim modello |
| stato corrente | composto | nessuno         | Output         | stessa dim modello |
##### Sincronizzazione:
| Informazione   | Tipo     | Livello privacy | I/O            | Vincoli            |
| -------------- | -------- | --------------- | -------------- | ------------------ |
| stato cella    | semplice | nessuno         | Input e Output | true, false        |
| stato iniziale | composto | nessuno         | Input          | stessa dim modello |
| stato corrente | composto | nessuno         | Output         | stessa dim modello |
| game on        | semplice | nessuno         | Input e Output | true, false        |
##### Stop:
| Informazione | Tipo     | Livello privacy | I/O            | Vincoli     |
| ------------ | -------- | --------------- | -------------- | ----------- |
| stato cella  | semplice | nessuno         | Input e Output | true, false |

### Analisi dei vincoli

#### Tabella vincoli:

| Requisito         | Categorie         | Impatto                                                    | Funzionalità                                      |
| ----------------- | ----------------- | ---------------------------------------------------------- | ------------------------------------------------- |
| Velocità          | Tempo di risposta | Aumenta la complessità, <br>aumentano il tempo di risposta | stato corrente                                    |
| UX intuitiva      | Usabilità         | Migliora l'usabilità                                       | Start, stop, exit, stato iniziale, stato corrente |
| Coerenza dati M-V | Coerenza dati     | evita errori di render                                     | stato corrente                                    |
### Analisi documento requisiti

#### Tabella maschere:

| Maschera | Informazioni   | Funzionalità                                                                                                                    |
| -------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| GOL GUI  | pagina con GUI | pagina interattiva con le funzionalità richieste:<br>- bottone start<br>- bottone stop<br>- bottone exit<br>- celle interattive |

### Analisi ruoli e responsabilità
#### tabella ruoli:

| ruolo  | responsabilità | maschere | riservatezza | numerosità   |
| ------ | -------------- | -------- | ------------ | ------------ |
| utente | nessuna        | GOL GUI  | nessuna      | 1 alla volta |
#### Tabella ruolo-informazione utente:

| informazione   | tipo accesso      |
| -------------- | ----------------- |
| game on        | lettura/scrittura |
| stato cella    | lettura/scrittura |
| stato iniziale | scrittura         |
| stato corrente | lettura           |
| stato cella    | lettura/scrittura |
### Scomposizione del problema

#### tabella scomposizione funzionalità:


| funzionalità            | scomposizione                              |
| ----------------------- | ------------------------------------------ |
| rappresentazione visiva | Visualizzazione griglia,<br>Update griglia |

| Sotto-funzionalità      | Sotto-funzionalità | Legame                                            | Informazioni                                |
| ----------------------- | ------------------ | ------------------------------------------------- | ------------------------------------------- |
| Visualizzazione griglia | Update griglia     | Visualizzazione griglia dipende da Update griglia | stato cella, stato corrente, stato iniziale |

### Modello del dominio

#### Pseudo-UML:
![[PseudoUml_02.png]]
<h3>Piano di lavoro</h3>

<p>Il piano di lavoro proposto consiste nel procedere nella seguente maniera</p>

<ul>

<li>realizzazione interfacce per GUI html</li>

<li>realizzazione interfacce per iomap.js</li>

<li>realizzazione interfacce per websocket.js</li>

<li>realizzazione di GUI html</li>

<li>realizzazione iomap.js</li>

<li>realizzazione di websocket.js</li>

<li>testing singolo interazione tra componenti</li>

<li>debug</li>

</ul>

  
  

<p>Basandomi sulle esperienze del team (me) e dai precedenti lavori posso stimare(worst case):</p>

<ul>

<li>realizzazione interfacce per GUI html: 10 min</li>

<li>realizzazione interfacce per iomap.js: 10 min</li>

<li>realizzazione interfacce per websocket.js: 10 min</li>

<li>realizzazione di GUI html: 1h</li>

<li>realizzazione iomap.js: 2h</li>

<li>realizzazione di websocket.js: 1h</li>

<li>testing singolo interazione tra componenti:1h</li>

<li>debug:2h</li>

</ul>

Considerando queste tempistiche individuali dividerei il lavoro in blocchi da 1.30h, 2h, 2h per un totale di 5.30h totali e uno scarto di 1h (circa 20%) extra per eventuali errori e margini.
