<script>
    export default {
        name: 'CardComponent'
    }
</script>

<template>
    <div class="col-6 col-md-4 col-lg-3 mb-4">
        <div class="card d-flex align-items-center p-2 h-100">
            <img src="" class="card-img-top img-fluid" alt="YuGiOh card">
            <div class="card-body text-center">
                <h5 class="card-title">Card Title</h5>
                <p class="card-text">Card Description</p>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .card {
        background-color: #f5f5f5;
        border: 1px solid #ccc;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
</style>