<template>
  <div class="background">
    <Wrapper :width="'1000px'">
      <div class="content">
        <h1 :class="{hidden: !this.toggle}">About me</h1>
        <div class="text" :class="{hidden: !this.toggle}">
          <p>I started studying Mathematics and Technology at Technical University of Denmark in 2016. I quickly became interested in data analysis and programming. From there I moved into software development, and now I am doing my master in Computer Science. My education spreads across many fields, and my curiosity have always driven me towards learning new things. My latest obsession has been web development, which resulted in this page, among other things. If you have an interesting project, drop me a line, and that might be next.</p>
        </div>
      </div>
    </Wrapper>
  </div>
</template>



<script>
import Wrapper from "./Wrapper"

export default {
  name: 'Background',
  props: ["toggle"],
  components: {
    Wrapper
  },
}
</script>

<style scoped>
@import "../colors.css";


.content {
  padding: 30px 15px 50px;
  box-sizing: border-box;
}

.background {
  position: relative;
  width: 100%;
  background-color: var(--col5);
}

.background:before {
  position: absolute;
  content: "";
  background: inherit;
  /* height: sin(2deg)*1000px
    top: height/2
  */
  height: 35px;
  top: -17.5px;
  left: 0;
  width: 100%;
  transform: skewY(2deg);
  -o-transform: skewY(2deg);
  -moz-transform: skewY(2deg);
  -webkit-transform: skewY(2deg);
  z-index: 1;
}

.background:after {
  position: absolute;
  content: "";
  background: inherit;
  /* height: sin(2deg)*1000px
    bottom: height/2
  */
  height: 35px;
  bottom: -17.5px;
  left: 0;
  width: 100%;
  transform: skewY(2deg);
  -o-transform: skewY(2deg);
  -moz-transform: skewY(2deg);
  -webkit-transform: skewY(2deg);
  z-index: 1;
}


h1 {
  text-transform: uppercase;
  font-size: 32px;
  text-align: center;
  line-height: 50px;
}

.text {
  width: 100%;
  box-sizing: content-box;
  font-size: 24px;
  text-align: center;
  line-height: 30px;
}

@media only screen and (min-width: 1000px) {

  .background:before {
    transform: skewY(1deg);
    -o-transform: skewY(1deg);
    -moz-transform: skewY(1deg);
    -webkit-transform: skewY(1deg);
  }

  .background:after {
    transform: skewY(1deg);
    -o-transform: skewY(1deg);
    -moz-transform: skewY(1deg);
    -webkit-transform: skewY(1deg);
  }

  h1 {
    transition: all 0.5s ease;
  }

  h1.hidden {
    transform: translateX(-200px);
    -o-transform: translateX(-200px);
    -moz-transform: translateX(-200px);
    -webkit-transform: translateX(-200px);
    opacity: 0;
  }

  .text {
    transition: all 1s ease;
    -webkit-transition-delay: calc(var(--nth-child) * 1s);
    -moz-transition-delay: calc(var(--nth-child) * 1s);
    -o-transition-delay: calc(var(--nth-child) * 0.1s);
    transition-delay: calc(var(--nth-child) * 0.3s + 0.1s);
  }

  .text.hidden {
    transform: translateY(100px);
    -o-transform: translateY(100px);
    -moz-transform: translateY(100px);
    -webkit-transform: translateY(100px);
    opacity: 0;
  }


}

</style>
