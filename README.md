# Pentagramma a colori

Una pagina web per modificare uno spartito MusicXML senza installare programmi:

- **altezza del pentagramma**: si sceglie in millimetri (dalla prima all'ultima riga), da 3 a 20 mm;
- **note colorate**: si colorano una per una con un clic, oppure tutte quelle con lo stesso nome (tutti i Do, tutti i Re…);
- **salvataggio**: il risultato si scarica come file `.musicxml`, da aprire con MuseScore, Finale, Sibelius, Dorico e altri.

Tutto avviene nel browser: il file non viene inviato a nessun server.

## Come si usa

1. Apri la pagina (`index.html`). All'inizio c'è un esempio, *Fra Martino*, per provare.
2. Premi **Apri file** (oppure trascina il file sulla pagina). Vanno bene i file `.musicxml`, `.xml` e `.mxl`.
3. **Altezza del pentagramma**: usa il cursore, scrivi il numero oppure scegli una misura pronta (5,5 · 7 · 9 · 12 mm). L'anteprima mostra il risultato su un foglio A4.
4. **Pennello**: scegli un colore e clicca le note sullo spartito. La gomma toglie il colore. Il cerchio arcobaleno permette di scegliere qualsiasi altro colore.
5. **Colora per nome della nota**: ogni nota della scala ha il suo colore (all'inizio quelli dell'arcobaleno, ma si possono cambiare). Premi **Colora** su una riga, oppure **Colora tutte le note**.
6. **Annulla** (o Ctrl+Z) torna indietro di un passo. **Torna al file originale** ripristina tutto.
7. Premi **Salva MusicXML**: viene scaricato un file con il nome originale seguito da `-colorato.musicxml`.

## Cosa cambia nel file

- Il colore viene scritto nell'attributo `color` dell'elemento `<note>`; se la testa della nota (`<notehead>`) aveva già un suo colore, viene aggiornato anche quello.
- L'altezza del pentagramma viene scritta in `<defaults><scaling>`. Le misure della pagina (`<page-layout>`), i margini e la posizione dei titoli (`<credit>`) vengono ricalcolati, così il foglio resta della stessa grandezza.
- Il resto del file non viene toccato.

## Pubblicarla online con GitHub Pages

1. Nel repository su GitHub apri **Settings → Pages**.
2. In **Build and deployment** scegli **Deploy from a branch**, poi il branch `main` e la cartella `/ (root)`, e premi **Save**.
3. Dopo un paio di minuti la pagina è raggiungibile all'indirizzo `https://lorenzofrassa.github.io/modifica_xml_scuola/`.

## Dettagli tecnici

- Un solo file, `index.html`, senza passaggi di compilazione.
- Lo spartito viene disegnato con [OpenSheetMusicDisplay](https://opensheetmusicdisplay.org/) 2.2.1; i file `.mxl` vengono aperti con [JSZip](https://stuk.github.io/jszip/) 3.10.1. Entrambe le librerie si caricano da CDN, quindi serve una connessione a internet.
- L'anteprima è indicativa: ogni programma di notazione impagina lo spartito a modo suo.
