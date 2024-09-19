<script>
    export default {
        name: 'AppFooter'
    };
</script>

<template>
    <footer class="footer">
        <div class="container d-flex justify-content-between py-3 text-white">
            <p>&copy; 2024 Yu-Gi-Oh Boolean App.</p>
            <div>
                <span>Created by </span><a href="https://github.com/Francesco-Matteucci">Francesco Matteucci</a>
            </div>
        </div>
    </footer>
</template>

<style lang="scss" scoped>
    .footer {
        background-color: #333;
        color: white;
        width: 100%;
        position: fixed;
        bottom: 0;
        left: 0;
        height: 60px;

        a {

            color: #fff;
        }
    }
</style>