<script >
  export default {
    name: 'App',
  }
</script>

<template>
  <body>
    <router-view />
  </body>
  
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}

#main {
    box-sizing: border-box;
    margin-left: 320px;
    padding: 20px 10px;
    .main-container {
        margin-top: 50px;
        margin-left: 20px;
    }
}

</style>
