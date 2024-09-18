# Yu-Gi-Oh Card Viewer

## Descrizione
Questo progetto è un'applicazione Vue 3 che permette di visualizzare un elenco di carte Yu-Gi-Oh utilizzando l'API di Yu-Gi-Oh. L'applicazione consente di visualizzare fino a 50 carte alla volta e fornisce un conteggio dinamico delle carte caricate. Inoltre, l'utente può vedere le carte e ottenere informazioni dettagliate su di esse.

## Funzionalità principali:
- Visualizzazione di un elenco di carte Yu-Gi-Oh caricate tramite l'API.
- Conteggio dinamico del numero totale di carte visualizzate.
- Ogni carta ha un'animazione di "flip" al passaggio del mouse che rivela il fronte della carta.
- Loader che viene mostrato durante il caricamento delle carte con un tempo minimo di 3 secondi.
  
## Tecnologie utilizzate:
- **Vue 3**: Framework JavaScript per costruire l'interfaccia utente.
- **Axios**: Per effettuare la chiamata all'API.
- **Bootstrap 5**: Utilizzato per lo stile delle card e per il layout responsive.
- **SCSS**: Per lo styling personalizzato.

## Struttura del progetto

### **Components**
- `CardComponent.vue`: Gestisce la visualizzazione di ogni singola carta, con la funzionalità di rotazione al passaggio del mouse (flip).
- `LoaderComponent.vue`: Mostra un'animazione di caricamento durante il caricamento dei dati API.
- `AppMain.vue`: Componente principale che gestisce il layout, il conteggio delle carte e la logica per caricare i dati dall'API.

### **AppMain.vue**
- Gestisce la chiamata API tramite Axios per caricare le carte.
- Mostra un loader durante il caricamento.
- Visualizza dinamicamente il numero di carte caricate sopra la griglia di carte.
- Effettua un ciclo su tutte le carte caricate e le mostra utilizzando `CardComponent`.

### **CardComponent.vue**
- Ogni carta ha un'animazione "flip" che mostra il fronte della carta al passaggio del mouse.
- Ogni carta è visualizzata in modo responsivo utilizzando le classi di Bootstrap.

### **LoaderComponent.vue**
- Mostra un'animazione di caricamento personalizzata durante il caricamento dei dati dall'API.

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