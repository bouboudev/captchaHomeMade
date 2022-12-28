<template>
  <div id="app">
    <CaptchaHomeMade msg="CaptchaHomeMade"/>
  </div>
</template>

<script>
import CaptchaHomeMade from './components/Captcha_HomeMade.vue'

export default {
  name: 'App',
  components: {
    CaptchaHomeMade
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
