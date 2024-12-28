<script setup>
import Navbar from "./section/NavBar.vue";
import Greeting from "./section/GreetSec.vue";
import MyProject from "./section/MyProject.vue";
import AboutMe from "./section/AboutMe.vue";
import MySkills from "./section/MySkills.vue";
import ContactMe from "./section/ContactMe.vue";
</script>

<template>
  <div class="background"><Navbar /> <Greeting /></div>
  <div id="AboutMe"><AboutMe /></div>
  <div id="MySkills"><MySkills /></div>
  <div id="MyProject"><MyProject /></div>
  <div id="ContactMe"><ContactMe /></div>
</template>

<style scoped>
.background {
  height: 100vh;
  width: 100%;
  background-image: url("./assets/background.png");
  background-size: cover;
  background-position: center;
}
</style>
