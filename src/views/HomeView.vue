<template>
  <div class="home">
    <homePage />
  </div>
</template>

<script>
// @ is an alias to /src
import homePage from "../components/homePage.vue";
export default {
  name: "HomeView",
  components: {
    homePage,
  },
};
</script>
