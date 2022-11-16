<template>
  <div class="contact">
    <div class="contact-banner">
      <Wrapper :width="'1000px'">
        <div class="bounceIn contact-info" v-if="toggle">
          <h3>Contact Me</h3>
          <p>Email: antonstockmarr@gmail.com</p>
          <p>Phone: +45 27 17 99 55</p>
        </div>
      </Wrapper>
    </div>
  </div>
</template>

<script>
import Wrapper from "./Wrapper";

export default {
  name: 'Contact',
  data() {
    return {
      toggle: false
    }
  },
  components: {
    Wrapper
  },
  mounted() {
    let options = { threshold: 0.8};
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          this.toggle = true;
        }
      })
    }, options);
    const element = this.$el.querySelector(".contact-banner");
    observer.observe(element);
  }
}
</script>

<style scoped>
@import "../animate.min.css";
@import "../colors.css";

.contact-info {
  box-sizing: border-box;
  padding: 80px 15px  
}
 
.contact-banner {
  width: 100%;
  background-color: var(--col2);
  height: calc(92px + 160px);
}

.contact-banner h3 {
  font-size: 22px;
  margin-bottom: 20px;
  color: #111;
  text-align: center;
  text-transform: uppercase;
}

.contact-banner p {
  font-size: 14px;
  line-height: 25px;
  color: #111;
  text-align: center;
  text-transform: uppercase;
}



</style>
