<script>
    export default {
        name: 'CardCountComponent',
        props: {
            totalCards: {
                type: Number,
                required: true
            }
        }
    };
</script>

<template>
    <div class="text-end my-4 text-white">
        <h4>Total Cards: {{ totalCards }}</h4>
    </div>
</template>

<style scoped>
    h4 {
        font-size: 1.25rem;
        font-weight: bold;
    }
</style>
