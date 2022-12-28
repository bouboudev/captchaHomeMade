<template>
  <div id="app">
    <CaptchaHomeMade/>
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
  color: #f2f2f2;
  background: #2c3e50;
}
</style>
