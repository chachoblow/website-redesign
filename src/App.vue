<template>
  <div id="app">
    <router-link class="nav-left" to="/">Wesley Klein</router-link>
    <router-link class="nav-right" to="/about">About</router-link>
    <router-view/>
  </div>
</template>

<style lang="scss">
* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
  font-size: 10px;
}

html, body {
  margin: 0;
  padding: 0;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}


.nav-left {
  position: fixed;
  top: 0;
  left: 0;
  padding: 1em 0 0 1em;

  text-decoration: none;
  text-transform: uppercase;
  font-weight: 300;
  font-size: 2em;
  color: black;

  z-index: 100;

  &:hover {
    text-decoration: line-through;
    text-decoration-color: gold;
  }
}

.nav-right {
  position: fixed;
  top: 0;
  right: 0;
  padding: 1em 1em 0 0;

  text-decoration: none;
  text-transform: uppercase;
  font-weight: 300;
  font-size: 2em;
  color: black;
  z-index: 100;

  &:hover {
    text-decoration: line-through;
    text-decoration-color:gold;
  }
}

a {
  &.router-link-exact-active {
    
  }
}
</style>
