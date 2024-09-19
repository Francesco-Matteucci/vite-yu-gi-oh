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
            }
        }
    };
</script>

<template>
    <div class="mb-4">
        <label for="archetypeSelect" class="form-label text-white">Select Archetype</label>
        <select id="archetypeSelect" class="form-select" v-model="selectedArchetype" @change="onSelectArchetype">
            <option value="">Select your archetype</option>
            <option v-for="archetype in archetypes" :key="archetype.archetype_name" :value="archetype.archetype_name">
                {{ archetype.archetype_name }}
            </option>
        </select>
    </div>
</template>

<style scoped>
    .form-select {
        background-color: #D48F3B;
        color: white;
        border: none;
        box-shadow: 0 0 5px 2px rgba(0, 0, 0, 0.2);
    }

    .form-select:focus {
        outline: none;
    }
</style>
