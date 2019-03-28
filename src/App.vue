<template>
  <div id="app">
    <h1>Boards</h1>
    <h3>Tasks Completed</h3>
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
@import "assets/less/base.less";
@import "assets/less/buttons.less";
@import "assets/less/checkbox.less";
</style>
