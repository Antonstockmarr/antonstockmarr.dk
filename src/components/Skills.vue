<template>
    <div class="skills">
        <TiltedBanner :bgColour = "colors().col5()">
            <div class="skills-grid">
                <SkillCard :description = "'Azure, Prometheus, Kubernetes.'" :title = "'Cloud technologies'" :icon = "'cloud-tech.svg'" :show = "showSkill1"/>
                <SkillCard :description = "'Design architecture, testing, monitoring.'" :title = "'Microservices'" :icon = "'microservices.svg'" :show = "showSkill2"/>
                <SkillCard :description = "'Principles and patterns in C# and Java.'" :title = "'OOP design'" :icon = "'OOP.svg'" :show = "showSkill3"/>
                <SkillCard :description = "'CSS, HTML, Vue, Angular and React.'" :title = "'Web development'" :icon = "'web.svg'" :show = "showSkill4"/>
            </div>
        </TiltedBanner>        
    </div>
</template>


<script>
import SkillCard from './SkillCard.vue'
import TiltedBanner from './TiltedBanner.vue'
let colors = require('../colors.js');

export default {
    name: 'Skills',
    components: {
        SkillCard,
        TiltedBanner
    },
    data() {
        return {
            toggle: false,
            showSkill1: false,
            showSkill2: false,
            showSkill3: false,
            showSkill4: false,
        }
    },
    mounted() {
        let options = { threshold: 1};
        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    this.toggle = true;
                }
            })
        }, options);
        const element = this.$el.querySelector(".skills-grid").firstChild;
        observer.observe(element);

    },
    methods: {
        colors() {
            return colors.default;
        }
    },
    watch: {
        toggle: function(value) {
            if (value) {
                this.showSkill1 = true;
                setTimeout(() => this.showSkill2 = true, 100);
                setTimeout(() => this.showSkill3 = true, 200);
                setTimeout(() => this.showSkill4 = true, 300);
            }
        }
    }
}
</script>

<style>

.skills-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
}

@media only screen and (min-width: 1000px) {

    .skills-grid {
        grid-template-columns: 1fr 1fr 1fr 1fr;
    }
}
</style>
