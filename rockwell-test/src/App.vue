<template>
  <div id="app">

    <tutorial-header></tutorial-header>

    <cv-content id="#main-content">
      <router-view />
    </cv-content>

  </div>
</template>

<script>
import TutorialHeader from './components/TutorialHeader/TutorialHeader.vue'

export default {
  components: {
    TutorialHeader
  }
}
</script>

<style lang="scss">
@import "./styles/carbon";
</style>
