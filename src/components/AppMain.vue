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

            <!-- Mostro il numero totale di carte -->
            <CardCountComponent :totalCards="cards.length" />

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

<style scoped></style>