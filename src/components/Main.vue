<template>
    <main class="main" v-show="show">
        <Header v-on:scrollTo="scrollTo" v-on:goToFront="goToFront" />
        <AboutMe/>
        <Skills/>
        <MyWork/>
        <Contact/>
        <Footer/>
    </main>
</template>



<script>
import Header from "./Header"
import MyWork from "./MyWork"
import Contact from "./Contact"
import AboutMe from "./AboutMe.vue"
import Skills from "./Skills.vue"
import Footer from "./Footer.vue"


export default {
    name: 'Main',
    components: {
    Header,
    MyWork,
    Contact,
    AboutMe,
    Skills,
    Footer
},
    props: ['show'],
    methods: {
        scrollTo(el) {
            let yOffset = -50;
            let target = document.querySelector(el);
            let main = document.querySelector('.main');
            const y = target.getBoundingClientRect().top + main.scrollTop + yOffset;
            main.scrollTo({ top: y, behavior: "smooth"});
        },
        goToFront() {
            this.$emit("goToFront");
        }
    },
}
</script>

<style scoped>

.main {
    position: absolute;
    top: 0vh;
    bottom: 0vh;
    left: 0vw;
    right: 0vw;
    overflow: auto;
}

</style>
