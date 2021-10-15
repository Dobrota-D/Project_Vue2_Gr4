<template>
  <div id="app">
    <div id="nav">
      <h1 class="title">Coin Market Wrap</h1>
      <router-link to="/"> Home </router-link> |
      <router-link to="/about"> À propos </router-link> |
      <router-link to="/admin"> Admin </router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.title{
  font-size: 5vh;
}
</style>

