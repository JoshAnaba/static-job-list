<template>
  <div id="app"> 
    <Content/>
  </div>
</template>

<script>
import Content from '@/components/Content.vue'

export default {
  name: 'App',
  components: {
    Content
  }
}
</script>

<style>
body{
  margin: 0;
  max-width: 1440px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

}
</style>
