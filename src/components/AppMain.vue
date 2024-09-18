<script>
    import axios from 'axios';
    import CardComponent from './CardComponent.vue'

    export default {
        name: 'AppMain',
        components: {
            CardComponent
        },
        data() {
            return {
                // Dati per le carte
                cards: [],
                // Flag di caricamento
                loading: true
            };
        },
        mounted() {
            // Effettuo la chiamata API per il montaggio del componente
            this.fetchCards();
        },
        methods: {
            fetchCards() {
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
                        // Una volta completato, disattivo il caricamento
                        this.loading = false;
                    });
            }
        }
    }
</script>

<template>
    <main class="container mt-4">
        <div v-if="loading" class="text-center">
            <p>Loading...</p>
        </div>
        <div v-else class="row justify-content-center p-4">
            <CardComponent v-for="card in cards" :key="card.id" :card="card" />
        </div>
    </main>
</template>

<style scoped></style>