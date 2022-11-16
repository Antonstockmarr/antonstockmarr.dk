<template>
  <div class="cover">
    <slot></slot>
  </div>  
</template>

<script>
export default {
  name: 'MouseBackground',
  methods: {
  }
}


</script>

<script setup>

import { onMounted } from 'vue'


onMounted(() => {
  let background = document.querySelector('.cover');
  background.addEventListener('mousemove', e => {
    let x = e.clientX;
    let y = e.clientY;
    background.style.setProperty('--x', x + 'px');
    background.style.setProperty('--y', y + 'px');
  });
})

</script>

<style scoped>
@import "../colors.css";


.cover {
    background: transparent;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    pointer-events: inherit;
  }

  .cover:before {
    --size: 0;
    content: '';
    position: absolute;
    width: 200vw;
    height: 200vh;
    transform: translate(-50%, -50%);
    background: radial-gradient(circle closest-side, transparent 25%, black 50%);
    --size: max(200vw, 200vh);

    animation: run 10s 0s infinite;
    -moz-animation: run 10s 0s infinite;
    -o-animation: run 10s 0s infinite;
    -webkit-animation: run 10s 0s infinite;
  }

  @keyframes run {
    0% {
      top: 30%;
      left: 25%;
    }
    25% {
      top: 20%;
      left: 75%;
    }
    50% {
      top: 80%;
      left: 28%;
    }
    75% {
      top: 70%;
      left: 65%;
    }
    100% {
      top: 30%;
      left: 25%;
    }
  }

.cover span {
  position: relative;
}

@media only screen and (min-width: 1000px) {

  .cover {
    background: black;
  }

  .cover:before {
    transform: translate(-50%, -50%);
    width: var(--size);
    height: var(--size);
    left: var(--x);
    top: var(--y);
    animation: none;
    -moz-animation: none;
    -o-animation: none;
    -webkit-animation: none;

  }

  .cover:hover {
    background: transparent;
  }

  .cover:hover:before {
  background: radial-gradient(circle closest-side, transparent 20%, black 30%);
  --size: max(200vw, 200vh);
}

}
</style>

