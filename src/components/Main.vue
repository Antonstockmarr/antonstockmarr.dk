<template>
    <main class="main" v-show="show">
        <Header v-on:scrollTo="scrollTo" v-on:goToFront="goToFront" />
        <AboutMe :toggle="showAboutMe"/>
        <Skills :toggle="showSkills" />
        <MyWork :toggle="showWork"/>
        <Contact :toggle="showContact"/>
    </main>
</template>



<script>
import Header from "./Header"
import MyWork from "./MyWork"
import Contact from "./Contact"
import AboutMe from "./AboutMe.vue"
import Skills from "./Skills.vue"

export default {
    name: 'Main',
    components: {
    Header,
    MyWork,
    Contact,
    AboutMe,
    Skills
},
    props: ['show'],
    data() {
        return {
            showSkills: false,
            showWork: false,
            showAboutMe: false,
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
            let aboutMe = document.querySelector(".about-me");
            if (this.isElementInViewport(aboutMe, 0.75)) {
                this.showAboutMe = true;
            }
            let skills = document.querySelector(".skills");
            if (this.isElementInViewport(skills, 1)) {
                this.showSkills = true;
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
