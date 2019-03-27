<template>
  <div id="app">
      <!-- router-link -->
    <ToDo />
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue';

export default {
  name: 'App',
  components: {
    ToDo
  },
  data() {
    return {}
  }
}
</script>


<style lang="less">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
</style>
