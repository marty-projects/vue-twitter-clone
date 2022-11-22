<template>
  <div id="app">
    <UserProfile/>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile.vue";

export default {
  name: 'App',
  components: {UserProfile}
}
</script>

<style>
#app {
  font-family: Avenire, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
  }
</style>