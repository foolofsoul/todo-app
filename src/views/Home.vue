<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <ToDo msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import ToDo from "@/components/ToDo.vue";

export default {
  name: "home",
  components: {
    ToDo
  }
};
</script>
