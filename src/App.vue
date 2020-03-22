<template>
  <div id="app">
    <v-app id="inspire">
      <Navbar></Navbar>
      <v-content>
        <router-view style="padding-top: 50px;"></router-view>
      </v-content>
    </v-app>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar";

export default {
  name: "App",
  components: {
    Navbar
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Itim&display=swap");

$itim: "Itim", cursive;

#inspire {
  font-family: $itim;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: url("./assets/background.png");
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
