<script>
    import CardComponent from './CardComponent.vue'

    export default {
        name: 'AppMain',
        components: {
            CardComponent
        }
    }
</script>

<template>
    <main class="container mt-4">
        <div class="row justify-content-center">
            <CardComponent v-for="n in 12" :key="n" />
        </div>
    </main>
</template>

<style scoped></style>