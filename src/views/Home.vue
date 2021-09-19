<template>
  <div class="hello">
    <div class="profile">
      <div class="qualities">
        <transition-group
          appear
          tag="ul"
          @before-enter="beforeEnterQualities"
          @enter="enterQualities"
        >
          <li
            v-for="(item, index) in qualities"
            :key="item.name"
            :data-index="index"
          >
            <div style="white-space: nowrap">{{ item.text.toUpperCase() }}</div>
          </li>
        </transition-group>
      </div>
      <transition
        class="avatar"
        appear
        @before-enter="beforeEnterAvatar"
        @enter="enterAvatar"
      >
        <img class="avatar-img" src="@/assets/profile.png" />
      </transition>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import gsap from "gsap";

export default {
  name: "Home",
  props: {
    msg: String,
  },
  setup() {
    /** qualities configuration */
    const qualities = ref([
      { text: "I'm", name: "elo" },
      { text: "Creative", name: "el1" },
      { text: "Motivated", name: "el3" },
      { text: "Enthusiastic", name: "el2" },
      { text: "Good practice ♥︎", name: "el4" },
    ]);
    const beforeEnterQualities = (el) => {
      el.style.transform = "translateX(-500px)";
      el.style.opacity = 0;
    };
    const enterQualities = (el, done) => {
      var index = parseInt(el.dataset.index);
      var desplX = 0;
      var desplY = -2 * (index + 1);
      while (index > 0) {
        desplX = desplX - 5;
        index--;
      }
      gsap.to(el, {
        transform: `translateX(${desplX}rem) translateY(${desplY}rem)`,
        rotate: 30,
        duration: 0.8,
        opacity: 1,
        ease: "all",
        onComplete: done,
        delay: 0.8 * el.dataset.index,
      });
    };

    /** Avatar animation conf */
    const beforeEnterAvatar = (el) => {
      el.style.transform = "translateY(100vh)";
      el.style.opacity = 0;
    };
    const enterAvatar = (el, done) => {
      gsap.to(el, {
        transform: "translateY(0vh)",
        overflow: "hidden",
        ease: "all",
        delay: 4,
        duration: 1.2,
        opacity: 1,
        onComplete: done,
      });
    };

    return {
      qualities,
      beforeEnterQualities,
      enterQualities,
      enterAvatar,
      beforeEnterAvatar,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.profile {
  /* background: linear-gradient(45deg, #ffca99, #ffec99);*/
  background: rgb(24, 24, 24);
  max-width: 100vw;
  max-height: 100vh;
  /* padding: 2rem; */
  overflow: hidden;
}

/** Qualities */
.profile .qualities {
  top: 0rem;
  left: -9rem;
  font-size: 10rem;
  font-weight: bold;
  text-align: left;
  padding: 2rem;
  margin-left: 10rem;
  color: rgb(24, 24, 24);
  transform: rotate(-30deg);
  border: solid 1px white;
  text-shadow: -1px -1px 0 #fff, 1px -1px 0 #fff, -1px 1px 0 #fff,
    1px 1px 0 #fff;
}
.profile .qualities li {
  text-decoration: none;
  list-style-type: none;
}
.profile .qualities li div {
  padding: -10px 0px;
  margin: -50px 0px;
  border-radius: 10em;
}

/** Avatar */
.avatar {
  position: absolute;
  top: 0px;
  left: 0px;
  background: pink;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.avatar-img {
  border-radius: 100rem;
  background-color: lightblue;
  width: 360px;
  height: 360px;
  left: calc(50vw - 180px);
  top: calc(50vh - 180px);
}

@media only screen and (max-width: 600px) {
  .avatar-img {
    width: 60vw;
    height: 60vw;
    left: 20vw;
    top: calc(50vh - 30vw);
  }
}
</style>
