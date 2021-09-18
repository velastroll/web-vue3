<template>
  <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
  </div>
  <router-view v-slot="{Component}">
    <transition name="route" mode="out-in">
      <component :is="Component">
      </component>
    </transition>
  </router-view>
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
  color: #ffffffbe;
  background: linear-gradient(#2c3e50, #202931);
  min-width: 100vw;
  min-height: 100vh;
}

* {
  margin: 0;
  padding: 0;
}

/** nav links */
#nav a {
  font-weight: bold;
  color:aliceblue;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color:aquamarine;
}

/** Router transition */
.route-enter-from {
  opacity: 0;
  transform: translateX(100px);
}
.route-leave-to {
  opacity: 0;
  transform: translateX(-100px);
}

.route-enter-to {
  opacity: 1;
  transform: translateX(0px);
}
.route-leave-from {
  opacity: 1;
  transform: translateX(0px);
}

.route-enter-active,
.route-leave-active {
  transition: all 0.3s ease-out;
}
</style>
