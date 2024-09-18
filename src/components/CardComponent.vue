<script>
    export default {
        name: 'CardComponent',
        props: {
            card: {
                type: Object,
                required: true
            }
        }
    }
</script>

<template>
    <div class="col-6 col-md-4 col-lg-3 mb-4">
        <div class="card p-2 h-100">
            <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
            <div class="card-body text-center">
                <h5 class="card-title">{{ card.name }}</h5>
                <p class="card-text">{{ card.type }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .card {
        background-color: #D48F3B;
        box-shadow: 1px 1px 20px black;

        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .card img {
        max-width: 100%;
        height: auto;
    }
</style>