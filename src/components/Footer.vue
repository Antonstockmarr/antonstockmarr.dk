<template>
    <div class="footer">
      <Wrapper :width="'1000px'">
        <div class="so-me-bar">
          <a  target="_blank" href="https://github.com/Antonstockmarr" class="github">
            <img src="@/assets/github1.svg" alt="">
          </a>
          <a target="_blank" href="https://www.linkedin.com/in/anton-stockmarr-b40a211a3/" class="linkedin">
            <img src="@/assets/linkedin2.svg" alt="">
          </a>
        </div>
      </Wrapper>
    </div>
</template>


<script>
import Wrapper from "./Wrapper";

export default {
  name: 'Footer',
  components: {
    Wrapper
  }
}
</script>

<style scoped>
@import "../colors.css";

.footer {
  background-color: var(--col4);
}

.so-me-bar {
  box-sizing: border-box;
  padding: 64px;
  width: 100%;
  display: grid;
  display: -ms-grid;
  -ms-grid-columns: 1fr 64px 64px 64px 1fr;
  grid-template-columns: 1fr 64px 64px 64px 1fr;
  grid-auto-rows: 64px;
}
img {
  width: 100%;
  height: 100%;
}

.github {
  grid-row: 1;
  grid-column: 2;
  -ms-grid-row: 1;
  -ms-grid-column: 2;

}

.github:hover {
  background-color: #fe019a;
  border-radius: 32px;
  box-shadow: 0 0 10px 5px #fe019a;
}

.linkedin {
  grid-row: 1;
  grid-column: 4;
  -ms-grid-row: 1;
  -ms-grid-column: 4;
}

.linkedin:hover {
  background-color: #0e76a8;
  border-radius: 32px;
  box-shadow: 0 0 10px 5px #0e76a8;
}

</style>