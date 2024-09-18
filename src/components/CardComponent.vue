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
    <div id="yugi-card" class="col-6 col-md-4 col-lg-3 mb-4">
        <div class="container-card">
            <div class="card-yugioh">
                <div class="front">
                    <img src="https://vignette.wikia.nocookie.net/yugioh/images/9/95/SlifertheSkyDragon-GBI-AE-Back.png/revision/latest/scale-to-width-down/328?cb=2010072608370"
                        alt="Card Back" />
                </div>
                <div class="back">
                    <img :src="card.card_images[0].image_url" :alt="card.name" />
                </div>
            </div>
        </div>
        <div class="card-text text-center mt-2">
            <h5 class="card-title mb-4">{{ card.name }}</h5>
            <p class="card-type">{{ card.type }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>

    .container-card {
        width: 100%;
        height: 0;
        padding-bottom: 150%;
        perspective: 1500px;
        position: relative;
    }

    .card-yugioh {
        position: absolute;
        width: 100%;
        height: 100%;
        transform-style: preserve-3d;
        transition: transform 1s;
    }

    .container-card:hover .card-yugioh {
        transform: rotateY(180deg);
    }

    #yugi-card:hover .card-text {
        opacity: 1;
    }

    .front,
    .back {
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
        top: 0;
        left: 0;
    }

    .front img {
        width: 100%;
        height: auto;
    }

    .back {
        transform: rotateY(180deg);

        img {
            width: 100%;
            height: auto;
        }
    }

    .card-title {
        color: #fff;
        font-size: 1rem;
        font-weight: bold;
    }

    .card-type {
        font-size: 0.9rem;
        font-weight: bold;
    }

    .card-text {
        opacity: 0;
    }

</style>
