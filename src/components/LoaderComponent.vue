<script>
    export default {
        name: 'LoaderComponent'
    }
</script>

<template>
    <div class="rl-loading-container">
        <div class="rl-loading-thumb rl-loading-thumb-1"></div>
        <div class="rl-loading-thumb rl-loading-thumb-2"></div>
        <div class="rl-loading-thumb rl-loading-thumb-3"></div>
    </div>
</template>

<style scoped>
    .rl-loading-container {
        height: 80vh;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 10px;
    }

    .rl-loading-thumb {
        width: 10px;
        height: 40px;
        background-color: #41f3fd;
        margin: 4px;
        box-shadow: 0 0 12px 3px #0882ff;
        animation: rl-loading 1.5s ease-in-out infinite;
    }

    .rl-loading-thumb-1 {
        animation-delay: 0s;
    }

    .rl-loading-thumb-2 {
        animation-delay: 0.5s;
    }

    .rl-loading-thumb-3 {
        animation-delay: 1s;
    }

    @keyframes rl-loading {
        0% {}

        20% {
            background: white;
            transform: scale(1.5);
        }

        40% {
            background: #41f3fd;
            transform: scale(1);
        }
    }
</style>