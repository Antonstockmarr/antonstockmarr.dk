<template>
    <div class="about">
        <img src="@/assets/me.jpg" alt="">
        <p>I study in Denmark, and I have a passion for everything related to software development, from front-end to complex algorithms and optimization.</p>
    </div>
</template>



<script>
export default {
    name: 'About',
}

</script>

<style scoped>

.about {
    padding: 25px 15px;
}

img {
    width: 80%;
    display: block;
    margin: 0px auto 0;
}

p {
    font-size: 16px;
    text-align: center;
    line-height: 20px;
    margin: 10px 0;
}

</style>