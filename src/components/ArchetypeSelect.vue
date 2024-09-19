<script>
    import axios from 'axios';

    export default {
        name: 'ArchetypeSelect',
        data() {
            return {
                // Raccolgo tutti i dati degli archetipi
                archetypes: [],
                // Archetipo selezionato
                selectedArchetype: ''
            };
        },
        mounted() {
            // Effettuo una chiamata API per ottenere gli archetipi
            this.fetchArchetypes();
        },
        methods: {
            fetchArchetypes() {
                axios
                    .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
                    .then((response) => {
                        // Inserisco gli archetipi ottenuti nell'array creato
                        this.archetypes = response.data;
                    })
                    .catch((error) => {
                        console.error('Errore nel caricamento degli archetipi:', error);
                    });
            },
            onSelectArchetype() {
                // Emetto l'event che passa l'archetipo selezionato al componente genitore
                this.$emit('archetype-selected', this.selectedArchetype);
            },
            refreshPage() {
                window.location.reload();
            }
        }
    };
</script>

<template>
    <div class="mb-4 fw-bold d-flex">
        <select id="archetypeSelect" class="form-select" v-model="selectedArchetype" @change="onSelectArchetype">
            <option value="">Select your archetype</option>
            <option v-for="archetype in archetypes" :key="archetype.archetype_name" :value="archetype.archetype_name">
                {{ archetype.archetype_name }}
            </option>
        </select>
        <img class="ms-4" src="../assets/icon.png" alt="Yu-Gi-Oh Card" title="Reset your page" @click="refreshPage">
    </div>
</template>

<style lang="scss" scoped>

    div img {
        height: 45px;
        cursor: pointer;
        z-index: 2;
    }


    .form-select {
        background: linear-gradient(135deg, #d48f3b, #b76b29);
        width: 250px;
        color: #fff;
        border: 2px solid #000;
        border-radius: 8px;
        padding: 0.5rem;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        transition: all 0.3s ease;
        font-weight: bold;
        text-align: center;
        cursor: pointer;
    }

    .form-select:focus {
        outline: none;
        box-shadow: 0 0 8px 4px rgba(0, 0, 0, 0.3);
        border-color: #ffb84d;
    }

    .form-select:hover {
        background: linear-gradient(135deg, #e6a954, #c37b33);
        color: #fff;
    }

    .form-select option {
        color: #000;
        background-color: #ffb84d;
    }
</style>
