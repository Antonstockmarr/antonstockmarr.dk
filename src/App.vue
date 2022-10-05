<template>


  <div id="app">
    <Transition :toggle="transition" />
    <Front v-on:goToMain="goToMain" :show="content===`front`"/>
    <Main v-on:goToFront="goToFront" :show="content===`main`"/>
  </div>
</template>

<script>
import Transition from "./components/Transition"
import Front from "./components/Front"
import Main from "./components/Main"


export default {
  name: 'App',
  metaInfo: {
    title: 'Anton Stockmarr',
    meta: [
      { name: "description", content: "Hi, I'm Anton Stockmarr, and this is a page about my work!"}
    ]
  },
  components: {
    Front,
    Main,
    Transition
  },
  data() {
    return {
      transition: true,
      content: `front`
    }
  },
  methods: {
    goToMain() {
      this.transition = false;
      setTimeout(() => {
        this.content = `main`;
      }, 600);
    },
    goToFront() {
      this.transition = true;
      setTimeout(() => {
        this.content = `front`;
        let main = document.querySelector('.main');
        main.scrollTo({top: 0});
      }, 600);
    }
  }
}
</script>

<style>
@import "reset.css";

#app {
  height: 100vh;
  width: 100vw;
  position: relative;
  overflow: hidden;
}

		
</style>
