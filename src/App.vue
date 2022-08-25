<template>
  <div id="app">

    <TitleContainer/>
  
  </div>
</template>

<script>
import TitleContainer from "./components/titleContainer.vue";


export default {
  name: 'App',
  components: {
    TitleContainer
}
}
</script>

<style lang="scss">
@import 'src/styles/main.scss';
 
</style>
