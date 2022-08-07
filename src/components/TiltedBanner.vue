<template>
  <div :style = "bgStyle" class="banner">
    <Wrapper :width="'1000px'">
      <div class="content">
        <slot></slot>
      </div>
    </Wrapper>
  </div>
</template>



<script>
import Wrapper from "./Wrapper"

export default {
  name: 'TiltedBanner',
  props: {
    bgColour: {
        type: String,
        default: "#000000"
  }},
  components: {
    Wrapper
  },
  computed: {
    bgStyle() {
        return {
            "background-color": this.bgColour
        }
    }
  }
}
</script>

<style scoped>


.content {
  padding: 30px 15px 50px;
  box-sizing: border-box;
}

.banner {
  position: relative;
  width: 100%;
}

.banner:before {
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

.banner:after {
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


@media only screen and (min-width: 1000px) {

  .banner:before {
    transform: skewY(1deg);
    -o-transform: skewY(1deg);
    -moz-transform: skewY(1deg);
    -webkit-transform: skewY(1deg);
  }

  .banner:after {
    transform: skewY(1deg);
    -o-transform: skewY(1deg);
    -moz-transform: skewY(1deg);
    -webkit-transform: skewY(1deg);
  }
}

</style>
