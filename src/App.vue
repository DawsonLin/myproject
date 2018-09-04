<template>
  <div id="app">
    <!--<index></index>-->
    <parent></parent>
  </div>
</template>

<script>

export default {
  name: 'App',
  components:{
      parent:require('@/components/parent').default,
      // index:require('@/components/index').default,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
