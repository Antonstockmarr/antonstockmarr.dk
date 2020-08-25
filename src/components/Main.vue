<template>
    <div class="main">
        <Header v-on:scrollTo="scrollTo" v-on:goToFront="goToFront"/>
        <About/>
        <Skills :toggle="showSkills"/>
        <MyWork />
        <Background :toggle="showBackground"/>
        <Contact :toggle="showContact"/>
    </div>
</template>



<script>
import Header from "./Header"
import About from "./About"
import Background from "./Background"
import MyWork from "./MyWork"
import Skills from "./Skills"
import Contact from "./Contact"

export default {
    name: 'Main',
    components: {
        Header,
        About,
        Background,
        MyWork,
        Skills,
        Contact
    },
    data() {
        return {
            showSkills: false,
            showBackground: false,
            showContact: false
        }
    },
    mounted () {
        let div = document.querySelector('.main');
        div.addEventListener('scroll', this.callbackFunc);
    },
    destroyed () {
        let div = document.querySelector('.main');
        div.removeEventListener('scroll', this.callbackFunc);
    },
    methods: {
        isElementInViewport(el, fraction) {
            let rect = el.getBoundingClientRect();
            let height = el.offsetHeight;
            return (
                rect.top >= 0 &&
                rect.left >= 0 &&
                rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) + (1-fraction)*height &&
                rect.right <= (window.innerWidth || document.documentElement.clientWidth)
            );
        },
        callbackFunc() {
            let chart = document.querySelector(".chart-container");
            if (this.isElementInViewport(chart, 0.75)) {
                this.showSkills = true;
            }/*
            let background = document.querySelector(".background");
            if (this.isElementInViewport(background, 1)) {
                this.showBackground = true;
            }*/
            let contact = document.querySelector(".contact-banner");
            if (this.isElementInViewport(contact, 1)) {
                this.showContact = true;
            }
        },
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
    }
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
