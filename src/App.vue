<template>
  <div id="app">
    <div class="background">
      <div class="nav">
        <img src="./assets/pokemon_logo.png" alt="Page logo" class="logoimg" />
      </div>
      <Home />
    </div>
  </div>
</template>

<script>
import Home from "@/views/Home.vue";
export default {
  components: {
    Home,
  },
};
</script>

<style lang="scss">
template {
  background: #9f4c04;
}
.background {
  margin: 0%;
  background: #9f4c04;
  padding-bottom: 10%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.logoimg {
  max-width: 30%;
  padding: 2%;
  margin-left: 35%;
}
.nav {
  width: 100%;
  background: #e99f04;
  text-align: center;
  box-shadow: 5px 4px 8px 2px rgba(70, 69, 69, 0.2);
}
</style>
