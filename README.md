# Yu-Gi-Oh Card Viewer

## Descrizione
Questo progetto è un'applicazione Vue 3 che permette di visualizzare un elenco di carte Yu-Gi-Oh utilizzando l'API di Yu-Gi-Oh. L'applicazione consente di visualizzare fino a 50 carte alla volta, fornisce un conteggio dinamico delle carte caricate e permette di filtrare le carte per archetipo. Inoltre, ogni carta può essere cliccata per visualizzare una **modal** con i dettagli completi.

## Funzionalità principali:
- Visualizzazione di un elenco di carte Yu-Gi-Oh caricate tramite l'API.
- Filtro dinamico delle carte per **archetipo**, con dati caricati dall'API.
- Conteggio dinamico del numero totale di carte visualizzate.
- Ogni carta ha un'animazione di "flip" al passaggio del mouse che rivela il fronte della carta.
- **Modal con i dettagli** della carta: descrizione, nome e archetipo, visualizzabile al click su una carta.
- Loader che viene mostrato durante il caricamento delle carte con un tempo minimo di 3 secondi.
- Pulsante per il **reset** dei filtri tramite un'icona accanto alla select.

## Tecnologie utilizzate:
- **Vue 3**: Framework JavaScript per costruire l'interfaccia utente.
- **Axios**: Per effettuare le chiamate all'API.
- **Bootstrap 5**: Utilizzato per lo stile delle card e per il layout responsive.
- **SCSS**: Per lo styling personalizzato.

## Struttura del progetto

### **Components**
- `CardComponent.vue`: Gestisce la visualizzazione di ogni singola carta, con la funzionalità di rotazione al passaggio del mouse (flip) e l'evento di click per aprire la modal dei dettagli.
- `LoaderComponent.vue`: Mostra un'animazione di caricamento durante il caricamento dei dati API.
- `AppMain.vue`: Componente principale che gestisce il layout, il conteggio delle carte, la logica per caricare i dati dall'API e il filtraggio delle carte per archetipo.
- `CardDetailModal.vue`: Componente della **modal** che mostra i dettagli completi della carta selezionata, come nome, descrizione, e archetipo.
- `ArchetypeSelect.vue`: Componente per filtrare le carte per archetipo, con le opzioni caricate dinamicamente dall'API.

### **AppMain.vue**
- Gestisce la chiamata API tramite Axios per caricare le carte.
- Mostra un loader durante il caricamento.
- Visualizza dinamicamente il numero di carte caricate sopra la griglia di carte.
- Effettua un ciclo su tutte le carte caricate e le mostra utilizzando `CardComponent`.
- Filtra le carte in base all'archetipo selezionato tramite il componente `ArchetypeSelect`.
- Gestisce l'apertura e la chiusura della modal per mostrare i dettagli della carta selezionata.

### **CardComponent.vue**
- Ogni carta ha un'animazione "flip" che mostra il fronte della carta al passaggio del mouse.
- Al click su una carta, si apre una modal che mostra i dettagli completi della carta.
- Ogni carta è visualizzata in modo responsivo utilizzando le classi di Bootstrap.

### **LoaderComponent.vue**
- Mostra un'animazione di caricamento personalizzata durante il caricamento dei dati dall'API.

### **CardDetailModal.vue**
- Componente della modal che mostra i dettagli completi della carta selezionata (nome, descrizione, ecc.).
- La modal può essere chiusa cliccando su un pulsante o cliccando al di fuori della stessa.

### **ArchetypeSelect.vue**
- Permette di filtrare le carte in base all'archetipo selezionato dall'utente.
- Le opzioni degli archetipi sono caricate dinamicamente tramite un'apposita chiamata API.
- Include un'icona che consente di resettare i filtri e tornare alla visualizzazione delle 50 carte iniziali.

## Setup del progetto

### Installazione
1. Clona il repository:
    ```bash
    git clone https://github.com/Francesco-Matteucci/vite-yu-gi-oh
    ```
2. Vai nella directory del progetto:
    ```bash
    cd yu-gi-oh-card-viewer
    ```
3. Installa le dipendenze:
    ```bash
    npm install
    ```

### Avvio del progetto
Per avviare il progetto in modalità sviluppo:
```bash
npm run dev
