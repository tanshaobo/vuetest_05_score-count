<template>
  <div id="app">
    <img src="./assets/logo.png">
    <score></score>
  </div>
</template>

<script>
import Score from '@/components/Score'
export default {
  name: 'App',
  components: {
    Score
  }
}
</script>

<style lang="stylus">
body
  background linear-gradient(135deg,rgba(255,255,255,.8) 0%,rgba(0,0,0,.2) 50%,rgba(255,255,255,.8) 100%)
  background-size 5px 5px
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>
