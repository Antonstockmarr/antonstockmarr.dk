<template>
    <div class="main" v-show="show">
        <Header v-on:scrollTo="scrollTo" v-on:goToFront="goToFront"/>
        <Home :toggle="showSkills"/>
        <MyWork :toggle="showWork"/>
        <Background :toggle="showBackground"/>
        <Contact :toggle="showContact"/>
    </div>
</template>



<script>
import Header from "./Header"
import Home from "./Home"
import Background from "./Background"
import MyWork from "./MyWork"
import Contact from "./Contact"

export default {
    name: 'Main',
    components: {
        Header,
        Home,
        Background,
        MyWork,
        Contact,
    },
    props: ['show'],
    data() {
        return {
            showSkills: false,
            showWork: false,
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
                rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) + (1-fraction)*height
            );
        },
        callbackFunc() {
            let chart = document.querySelector(".chart-container");
            if (this.isElementInViewport(chart, 0.75)) {
                this.showSkills = true;
            }
            let background = document.querySelector(".background");
            if (this.isElementInViewport(background, 1)) {
                this.showBackground = true;
            }
            let contact = document.querySelector(".contact-banner");
            if (this.isElementInViewport(contact, 1)) {
                this.showContact = true;
            }
            let work = document.querySelector(".my-work");
            if (this.isElementInViewport(work, 0.5)) {
                this.showWork = true;
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
    },
    watch: {
        show: function(val) {
            if (val) {
                setTimeout(this.callbackFunc, 1000);
            }
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
