<template>
  <router-view v-slot="{Component}">
    <transition name="route" mode="out-in">
      <component :is="Component">
      </component>
    </transition>
  </router-view>
  <!-- footer -->
  <div class="footer">
    Everything has been coded by me ♡
  </div>
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
  background: rgb(24, 24, 24);
  min-width: 100vw;
  max-width: 100vw;
  overflow: hidden;
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

/** footer */
.footer {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 6rem;
  background: rgb(53, 53, 53);
  color: white;
}
</style>
