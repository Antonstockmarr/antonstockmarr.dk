<template>
  <div class="contact">
    <div class="contact-banner">
      <div class="bounceIn" v-if="toggle">
        <h3>Contact Me</h3>
        <p>Email: antonstockmarr@gmail.com</p>
        <p>Phone: +45 27 17 99 55</p>
      </div>
    </div>
    <div class="so-me-bar">
      <a  target="_blank" href="https://github.com/Antonstockmarr" class="github">
        <img src="@/assets/github1.svg" alt="">
      </a>
      <a target="_blank" href="https://www.linkedin.com/in/anton-stockmarr-b40a211a3/" class="linkedin">
        <img src="@/assets/linkedin2.svg" alt="">
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Contact',
  props: ['toggle']
}
</script>

<style scoped>
@import "../animate.min.css";

.contact-banner {
  box-sizing: border-box;
  padding: 80px 15px;
  width: 100%;
  background-color:#E3EBFF;
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

.so-me-bar {
  box-sizing: border-box;
  padding: 64px;
  background-color: #000033;
  width: 100%;
  display: grid;
  grid-template-columns: 64px 1fr 64px;
  grid-auto-rows: 64px;
  grid-template-areas: 
    "github nothing linkedin";
}

img {
  width: 100%;
  height: 100%;
}

.github {
  grid-area: github;
}

.github:hover {
  background-color: #fe019a;
  border-radius: 32px;
  box-shadow: 0 0 10px 5px #fe019a;
}

.linkedin {
  grid-area: linkedin;
}

.linkedin:hover {
  background-color: #0e76a8;
  border-radius: 32px;
  box-shadow: 0 0 10px 5px #0e76a8;
}


</style>
