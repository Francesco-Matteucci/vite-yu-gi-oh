<script>
    import axios from 'axios';
    import CardComponent from './CardComponent.vue'
    import LoaderComponent from './LoaderComponent.vue'
    import ArchetypeSelect from './ArchetypeSelect.vue';

    export default {
        name: 'AppMain',
        components: {
            CardComponent,
            LoaderComponent,
            ArchetypeSelect
        },
        data() {
            return {
                // Dati per le carte
                cards: [],
                // Flag di caricamento
                loading: true,
                // Archetipo selezionato
                selectedArchetype: ''
            };
        },
        mounted() {
            // Effettuo la chiamata API per il montaggio del componente
            this.fetchCards();
        },
        methods: {
            fetchCards() {
                // Simulo un caricamento di 3 secondi
                const minLoadingTime = 3000;

                // Creo una variabile per tenere traccia del tempo iniziale
                const startTime = Date.now();

                axios
                    .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0')
                    .then((response) => {
                        // Inserisco nell'array i dati ricevuti
                        this.cards = response.data.data;
                    })
                    .catch((error) => {
                        console.error('Errore nella chiamata API:', error);
                    })
                    .finally(() => {

                        // Calcolo il tempo trascorso dalla chiamata API
                        const elapsedTime = Date.now() - startTime;

                        // Se il caricamento è stato troppo veloce, aspetto che passino i 3 secondi
                        const remainingTime = minLoadingTime - elapsedTime;

                        if (remainingTime > 0) {
                            setTimeout(() => {
                                this.loading = false;
                            }, remainingTime);
                        } else {
                            // Nel caso il caricamento avesse gia impiegato almeno 3 secondi, nascondo il loader
                            this.loading = false;
                        }
                    });
            },
            // Creo un metodo per gestire l'archetipo selezionato
            handleArchetypeSelected(archetype) {
                this.selectedArchetype = archetype;
                console.log("Archetipo selezionato:", this.selectedArchetype);

            }
        }
    }
</script>

<template>
    <main class="container mt-4">
        <div v-if="loading">
            <LoaderComponent />
        </div>
        <div v-else>
            <ArchetypeSelect @archetype-selected="handleArchetypeSelected" />

            <div class="text-end my-4 text-white">
                <h4>Total Cards: {{ cards.length }}</h4>
            </div>
            <div class="row justify-content-center">
                <CardComponent v-for="card in cards" :key="card.id" :card="card" />
            </div>
        </div>
    </main>
</template>

<style scoped></style>