<template>
  <router-view />
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

/* Custome Page Style */

body{
  padding: 0;
  margin: 0;
}

.logo{
    width: 150px;
}
.register input, .login input, .add input{
    width: 400px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid rgb(184, 224, 240);
}
.register button, .login button, .add button{
    width: 320px;
    height: 40px;
    font-size: 20px;
    border: 1px solid skyblue;
    color: #fff;
    background-color: skyblue;
    cursor: pointer;
}
</style>
