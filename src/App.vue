<template>
  <div>
    <NavBar />
    <RouterView />
  </div>
</template>

<script>
import { RouterView } from "vue-router";
import NavBar from "./components/navbar.vue";
export default {
  components: {
    NavBar,
    RouterView,
  }

}
</script>

<style>

</style>