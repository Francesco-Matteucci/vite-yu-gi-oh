<script>
  import AppHeader from './components/AppHeader.vue'
  import AppMain from './components/AppMain.vue'
  import AppFooter from './components/AppFooter.vue'

  export default {
    components: {
      AppHeader,
      AppMain,
      AppFooter
    }
  }
</script>

<template>
  <div>
    <AppHeader />
    <AppMain />
    <AppFooter />
  </div>
</template>

<style lang="scss">
  body {
    background: linear-gradient(135deg, #d48f3b, #b76b29);
  }
</style>
