<script>
    export default {
        name: 'AppHeader'
    }
</script>

<template>
    <header class="p-3">
        <div class="container d-flex justify-content-start align-items-center">
            <img class="img-fluid" src="../assets/img/logo.png" alt="">
        </div>
    </header>
</template>

<style scoped>
    header {
        height: 80px;
        font-family: "Krub", sans-serif;
        border-bottom: 6px solid #fff;
        margin-bottom: 80px;
    }

    img {
        position: relative;
        bottom: 8px;
        left: 0;
        height: 100px;
    }
</style>