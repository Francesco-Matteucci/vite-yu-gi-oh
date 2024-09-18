<script>
    export default {
        name: 'AppHeader'
    }
</script>

<template>
    <header class="p-3">
        <div class="container d-flex justify-content-start align-items-center">
            <img class="img-fluid" src="../assets/img/logo.png" alt="">
            <h1 class="px-4">Yu-Gi-Oh API</h1>
        </div>
    </header>
</template>

<style scoped>
    header {
        font-family: "Krub", sans-serif;
    }

    img {
        height: 100px;
    }
</style>