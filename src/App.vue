<template>
  <div id="app">
    <v-Nav />
    <v-Con />
  </div>
</template>
<script>
  import storage from './model/storage.js';
  import Navbar from './components/Navbar.vue';
  import Content from './components/Content.vue';
  console.log(storage)
  export default {
    name: 'App',
    components: {
      'v-Nav': Navbar,
      'v-Con': Content
    },
    data () {
      return {
        
      }
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
}
.red{
  color: red;
}
.blue{
  color: blue;
}
.box1{
  height: 200px;
  width: 300px;
  background: rgb(112, 192, 123);
}
body{
  background-color: lightblue;
}
</style>
