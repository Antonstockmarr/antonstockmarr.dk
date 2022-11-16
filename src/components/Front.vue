<template>
  <MouseBackground>    
    <div class="front" v-show="show">
      <div class="lines few">
        <div class="line"></div>
        <div class="line"></div>
        <div class="line"></div>
      </div>
    <div class="lines many">
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
    </div>
  </div>
  <div class="text" v-show="show">
    <p class="animated fadeIn delay-1">Hello, I'm <span class="name">Anton Stockmarr</span>.</p>
    <h1 class="animated fadeIn delay-2">I'm a software engineer.</h1>
  </div>
  <button class="animated fadeIn delay-3" v-show="show" @click="goToMain">Continue</button>
</MouseBackground>
</template>

<script>
import MouseBackground from "./MouseBackground";

export default {
  name: 'Front',
  components: {MouseBackground},
  props: ['show'],
  methods: {
    goToMain() {
      this.$emit('goToMain');
    }  
  }
}
</script>

<style scoped>
@import "../animate.min.css";
@import "../colors.css";

.front {
  box-sizing: border-box;
  background-color: var(--col4);
  height: 100vh;
  width: 100vw;
  padding: 0px;
  position: relative;
  z-index: -1;
}

.text {
  width: 100%;
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  -o-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  line-height: 30px;
  font-size: 24px;
  color: var(--col2);
  text-align: center;
  pointer-events: none;
}

p {
  line-height: 30px;
  font-size: 24px;
}

h1 {
  line-height: 56px;
  font-size: 40px;
}

.name {
  font-style: italic;
}

button {
  position: absolute;
  top: 75%;
  left: 50%;
  -webkit-transform: translate(-50%, -75%);
  -o-transform: translate(-50%, -75%);
  -ms-transform: translate(-50%, -75%);
  transform: translate(-50%, -75%);
  color: black;
  font-size: 20px;
  background: var(--col5);
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  z-index: 1;
}

button:hover {
  background: var(--col1);
  letter-spacing: 1px;
  box-shadow: 0px 5px 40px -10px rgba(0,0,0,0.57);
}

.lines {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 100%;
  margin: auto;
  width: 90%;
}

.many {
  display: none;
}

.line {
  position: absolute;
  width: 1px;
  height: 100%;
  top: 0;
  left: 50%;
  background: rgba(255, 255, 255, 0.1);
  overflow: hidden;
}

.line::after {
  content: '';
  display: block;
  position: absolute;
  height: 15vh;
  width: 100%;
  top: -50%;
  left: 0;
  background: linear-gradient(to bottom, rgba(255, 255, 255, 0) 0%, #ffffff 75%, #ffffff 100%);
  animation: run 4s 0s infinite;
  -moz-animation: run 4s 0s infinite;
  -o-animation: run 4s 0s infinite;
  -webkit-animation: run 4s 0s infinite;
  animation-fill-mode: forwards;
  -moz-animation-fill-mode: forwards;
  -o-animation-fill-mode: forwards;
  -webkit-animation-fill-mode: forwards;
  animation-timing-function: cubic-bezier(0.4, 0.26, 0, 0.97);
  -moz-animation-timing-function: cubic-bezier(0.4, 0.26, 0, 0.97);
  -o-animation-timing-function: cubic-bezier(0.4, 0.26, 0, 0.97);
  -webkit-animation-timing-function: cubic-bezier(0.4, 0.26, 0, 0.97);
}

.few .line:nth-child(1) {
  margin-left: -25%;
}

.few .line:nth-child(1)::after {
  animation-delay: 2s;
  -moz-animation-delay: 2s;
  -o-animation-delay: 2s;
  -webkit-animation-delay: 2s;
}

.few .line:nth-child(3) {
  margin-left: 25%
}

.few .line:nth-child(3)::after {
  -o-animation-delay: 2.5s;
  -moz-animation-delay: 2.5s;
  -webkit-animation-delay: 2.5s;
  animation-delay: 2.5s;
}
  
    
@keyframes run {
  from{
    top: -50%;
  }
  to {
    top: 110%;
  }
}

.delay-1 {
    -webkit-animation-delay: 500ms;
    -moz-animation-delay: 500ms;
    -o-animation-delay: 500ms;
    animation-delay: 500ms;
}
.delay-2 {
    -webkit-animation-delay: 1000ms;
    -moz-animation-delay: 1000ms;
    -o-animation-delay: 1000ms;
    animation-delay: 1000ms;
}
.delay-3 {
    -webkit-animation-delay: 1500ms;
    -moz-animation-delay: 1500ms;
    -o-animation-delay: 1500ms;
    animation-delay: 1500ms;
}
  

@media only screen and (min-width: 1000px) {


  p {
    font-size: 40px;
    line-height: 64px;
  }

  h1 {
    line-height: 88px;
    font-size: 88px;
  }

  button {
    font-size: 32px;
    padding: 15px 40px;
  }

  .few {
    display: none;
  }

  .many {
    display: block;
  }

  :nth-child(1) { --nth-child: -5; --nth-delay: 1}
  :nth-child(2) { --nth-child: -4; --nth-delay: 5}
  :nth-child(3) { --nth-child: -3; --nth-delay: 4 }
  :nth-child(4) { --nth-child: -2; --nth-delay: 8 }
  :nth-child(5) { --nth-child: -1; --nth-delay: 2 }
  :nth-child(6) { --nth-child: 0; --nth-delay: 9 }
  :nth-child(7) { --nth-child: 1; --nth-delay: 10 }
  :nth-child(8) { --nth-child: 2; --nth-delay: 3 }
  :nth-child(9) { --nth-child: 3; --nth-delay: 6 }
  :nth-child(10) { --nth-child: 4; --nth-delay: 7 }
  :nth-child(11) { --nth-child: 5; --nth-delay: 11 }

  .many .line {
    margin-left: calc(var(--nth-child) * -10%);
  }

  .many .line::after {
    animation-delay: calc(var(--nth-delay) * 0.2s);
    -o-animation-delay: calc(var(--nth-delay) * 0.2s);
    -moz-animation-delay: calc(var(--nth-delay) * 0.2s);
    -webkit-animation-delay: calc(var(--nth-delay) * 0.2s);
  }
}
</style>

