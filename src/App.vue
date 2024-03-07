<template>
  <main class="container">
    <MainPage />
  </main>
</template>

<script>
import MainPage from "./views/MainPage.vue";

export default {
  components: {
    MainPage,
  },
};
</script>

<style lang="scss">
.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 20px 20px;
}
</style>
