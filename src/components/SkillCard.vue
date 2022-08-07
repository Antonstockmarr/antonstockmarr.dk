<template>
    <div class="skill" :class="{hidden: !show}">
        <div class="icon">
            <img :src="require(`@/assets/${icon}`)" alt="">
        </div>
        <h1 class="text">{{title}}</h1>
        <p class="text">{{description}}</p>
    </div>
</template>


<script>

export default {
    props: ['description', 'title', 'icon', 'show'],
    data() {
        return {
        }
    },
    mounted () {
    },
    methods: {
    },
}
</script>

<style>

.icon {
    width: 60%;
    margin: 0 auto;
}

img {
    width: 100%;
    display: block;
}

.skill h1 {
    display: flex;
    font-size: 24px;
    line-height: 24px;
    text-align: center;
    align-items : center;
    justify-content : center;
    padding: 12px 0;
    height: 48px;
}

.skill p {
    display: block;
    font-size: 20px;
    line-height: 24px;
    text-align: center;
}

@media only screen and (min-width: 1000px) {

    .skill h1 {
        padding: 4px 0;
    }

    .icon, .text {
        -webkit-transition: all 0.3s ease;
        -o-transition: all 0.3s ease;
        transition: all 0.3s ease;
    }

    .hidden .text {
        -moz-transform: translateY(50px);
        -webkit-transform: translateY(-50px);
            -ms-transform: translateY(50px);
                transform: translateY(50px);
        opacity: 0;
    }

    .hidden .icon {
        transform: skewY(20deg);
        -o-transform: skewY(20deg);
        -moz-transform: skewY(20deg);
        -webkit-transform: skewY(20deg);
        opacity: 0;
    }
}
</style>
