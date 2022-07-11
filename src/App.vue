<template>
  <UserProfile/>
</template>

<script>
import UserProfile from './components/UserProfile';
export default {
  name: 'App',
  components: {UserProfile}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin-top: 60px;
  margin-left: 60px;
  margin-right: 60px;
  min-height: 100vh;
}
body{
  background-color: #EAF6F6;
}
</style>
