<template>
  <div class="background">
    <h1>About me</h1>
    <div class="text">
      <p>I started studying Mathematics and Technology at Technical University of Denmark in 2016. I quickly became interested in data analysis and programming. From there I moved into software development, and now I am doing my master in Computer Science. My education spreads across many fields, and my curiosity have always driven me towards learning new things. My latest obsession has been web development, which resulted in this page, among other things. If you have an interesting project, drop me a line, and that might be next.</p>
    </div>
  </div>
</template>



<script>
export default {
    name: 'Background',
    props: ["toggle"]
}
</script>

<style scoped>

.background {
  box-sizing: border-box;
  padding: 30px 15px 50px;
  width: 100%;
  background-color: grey;
}

h1 {
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

</style>
