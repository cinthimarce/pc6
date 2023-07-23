<template>
  <div id="app">
    <nav class="navbar" style="background-color: black;">
      <span class="mdi mdi-headphones">
        <router-link to="/"> Game Opinion</router-link> 
      </span>
      <span class="mdi mdi-home">
        <router-link to="/">Home</router-link>
      </span>
    </nav>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 50px;
}

nav a {
  font-weight: bold;
  color: #d8d8d8;
  margin-left: 5px;
  margin-right: 10px;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: white;
  
}
.mdi{
  color: white;
  margin-left: 10px;
  font-size: 20px;
}
</style>
