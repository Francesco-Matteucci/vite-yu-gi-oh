<script>
    export default {
        name: 'CardDetailModal',
        props: {
            card: {
                type: Object,
                required: true
            },
            showModal: {
                type: Boolean,
                required: true
            }
        },
        methods: {
            closeModal() {
                this.$emit('close-modal');
            }
        }
    };
</script>

<template>
    <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
        <div class="modal-content">
            <button class="btn-close" @click="closeModal">X</button>
            <div class="card-details text-center">
                <img :src="card.card_images[0].image_url" :alt="card.name" class="card-img-top">
                <h3>{{ card.name }}</h3>
                <p><strong>Type:</strong> {{ card.type }}</p>
                <p><strong>Description:</strong> {{ card.desc }}</p>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .modal-overlay {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1;
    }

    .modal-content {
        background-color: #D48F3B;
        border-radius: 8px;
        padding: 20px;
        max-width: 400px;
        max-height: 80vh;
        width: 100%;
        text-align: center;
        position: relative;
        box-shadow: 1px 1px 20px #000;
        display: flex;
        flex-direction: column;
    }

    .btn-close {
        position: absolute;
        top: -95px;
        right: -135px;
        border: none;
        background: transparent;
        font-size: 1.5rem;
        cursor: pointer;
        font-weight: bold;
        font-size: 5rem;
    }

    .card-details {
        flex-grow: 1;
        overflow-y: auto;
        padding-right: 10px;
    }

    .card-details img {
        max-width: 100%;
        height: auto;
        margin-bottom: 1rem;
    }

    .card-details h3 {
        margin-bottom: 1rem;
    }

    .card-details p {
        margin: 0.5rem 0;
        font-size: 0.9rem;
        text-align: left;
    }

    .card-description {
        padding: 10px;
        max-height: 150px;
        overflow-y: auto;
    }
</style>