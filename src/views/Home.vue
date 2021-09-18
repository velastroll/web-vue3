<template>
  <div class="hello">
    <transition appear
      @before-enter="beforeEnter"
      @enter="enter"
    >
      <h1> Home </h1>
    </transition>
    <button @click="changeData('Manolito')"> Periquito pim pim 
    </button>

    <h5> data: </h5>
    <p>
    {{data}}
    </p>
  </div>
</template>

<script>
import { ref, watch } from 'vue';
import gsap from 'gsap';

export default {
  name: 'Home',
  props: {
    msg: String
  },
  setup() {

    /** Header config */
    const beforeEnter = (el) => {
      el.style.transform = 'translateY(-60px)';
      el.style.opacity = 0
    }
    const enter = (el) => {
      gsap.to(el, {
        duration: 1,
        y: 0,
        opacity: 1,
        ease: 'bounce.out'
      });
    }
   
    /** Body config */
    const exampleText = ref('Manolito')
    const counter = ref(0)
    const changeExample = () => {
      counter.value++
    }

    /** Watchers */
    watch(counter, (currentValue) => {
      exampleText.value = `Ha sido pulsado ${currentValue} veces.`
    });

    return {
      data: exampleText,
      changeData: changeExample,
      beforeEnter,
      enter
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
