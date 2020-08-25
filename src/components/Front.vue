<template>
  <div class="front">
    <div class="lines">
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
    </div>
    <div class="text">
      <p class="animated fadeIn delay-1">Hello, my name is <span class="name">Anton Stockmarr</span>,</p>
      <p class="animated fadeIn delay-2">and I study Computer Science.</p>
    </div>
    <button class="animated fadeIn delay-3" @click="goToMain">Continue</button>
  </div>
</template>

<script>
export default {
  name: 'Front',
  methods: {
    goToMain() {
      this.$emit('goToMain');
    }  
  }
}
</script>

<style scoped>
@import "../animate.min.css";

.front {
  box-sizing: border-box;
  background-color: #000033;
  height: 100vh;
  width: 100vw;
  padding: 0px;
  position: relative;
}

.text {
  width: 100%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  line-height: 30px;
  font-size: 24px;
  color: white;
  text-align: center;
}

.name {
  font-style: italic;
}

button {
  position: absolute;
  top: 75%;
  left: 50%;
  transform: translate(-50%, -75%);
  color: #fff;
  font-size: 20px;
  background: #e04212;
  padding: 10px 20px;
  border-radius: 5px;
}

button:hover {
  background: #494949;
  letter-spacing: 1px;
  -webkit-box-shadow: 0px 5px 40px -10px rgba(0,0,0,0.57);
  -moz-box-shadow: 0px 5px 40px -10px rgba(0,0,0,0.57);
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
  animation: run 7s 0s infinite;
  animation-fill-mode: forwards;
  animation-timing-function: cubic-bezier(0.4, 0.26, 0, 0.97);
}

.line:nth-child(1) {
  margin-left: -25%;
}

.line:nth-child(1)::after {
  animation-delay: 2s;
}

.line:nth-child(3) {
  margin-left: 25%
}

.line:nth-child(3)::after {
  animation-delay: 2.5s
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
    -moz-animation-delay: none;
    animation-delay: 500ms;
}
.delay-2 {
    -webkit-animation-delay: 1000ms;
    -moz-animation-delay: none;
    animation-delay: 1000ms;
}
.delay-3 {
    -webkit-animation-delay: 1500ms;
    -moz-animation-delay: none;
    animation-delay: 1500ms;
}
  
  

</style>
