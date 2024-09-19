<script>
    import axios from 'axios';
    import CardComponent from './CardComponent.vue'
    import LoaderComponent from './LoaderComponent.vue'
    import ArchetypeSelect from './ArchetypeSelect.vue'
    import CardDetailModal from './CardDetailModal.vue'
    import CardCountComponent from './CardCountComponent.vue'

    export default {
        name: 'AppMain',
        components: {
            CardComponent,
            LoaderComponent,
            ArchetypeSelect,
            CardDetailModal,
            CardCountComponent
        },
        data() {
            return {
                // Dati per le carte
                cards: [],
                // Flag di caricamento
                loading: true,
                // Archetipo selezionato
                selectedArchetype: '',
                // Carta selezionata per la modal
                selectedCard: null,
                // Flag per mostrare o nascondere la modal
                showModal: false
            };
        },
        mounted() {
            // Effettuo la chiamata API per il montaggio del componente
            this.fetchCards();
        },
        methods: {
            fetchCards(archetype = '') {
                // Imposto il flag di caricamento su true
                this.loading = true;

                // Se è stato selezionato un archetipo, aggiungiamolo alla query dell'API
                const apiUrl = archetype ? `https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${archetype}` : 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0';

                axios
                    .get(apiUrl)
                    .then((response) => {
                        // Aggiorno i dati delle carte
                        this.cards = response.data.data;
                    })
                    .catch((error) => {
                        console.error('Errore nella chiamata API:', error);
                    })
                    .finally(() => {
                        setTimeout(() => {
                            this.loading = false;
                        }, 3000);
                    });
            },
            handleArchetypeSelected(archetype) {
                this.selectedArchetype = archetype;
                console.log('Archetipo selezionato:', archetype);

                // Effettuo una chiamata API per filtrare le carte dell'archetipo selezionato
                this.fetchCards(archetype);
            },
            openCardModal(card) {
                this.selectedCard = card;
                this.showModal = true;
            },
            closeCardModal() {
                this.showModal = false;
                this.selectedCard = null;
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
            <!-- Aggiungo la select degli archetipi -->
            <ArchetypeSelect @archetype-selected="handleArchetypeSelected" />

            <img id="yugi" src="../assets/img/images-Photoroom.png" alt="">

            <!-- Mostro il numero totale di carte -->
            <CardCountComponent :totalCards="cards.length" />

            <!-- Mostro un messaggio con l'archetipo scelto dall'utente-->

            <p v-if="selectedArchetype" class="text-center mt-3 fs-4 archetype-text">
                The list of cards with archetype: <strong>{{ selectedArchetype }}</strong>
            </p>

            <!-- Visualizzo le carte -->
            <div class="row justify-content-center">
                <CardComponent v-for="card in cards" :key="card.id" :card="card" @click="openCardModal(card)" />
            </div>
        </div>

        <!-- Modal per i dettagli della carta -->
        <CardDetailModal v-if="selectedCard" :card="selectedCard" :showModal="showModal"
            @close-modal="closeCardModal" />
    </main>
</template>

<style scoped>
    .container {
        position: relative;
    }

    .archetype-text {
        color: #ffd700;
        font-weight: bold;
        text-shadow: 2px 4px 2px rgba(0, 0, 0, 0.3);
    }

    #yugi {
        height: 120px;
        position: absolute;
        top: -51px;
        left: 200px;
        z-index: 1;
    }
</style>