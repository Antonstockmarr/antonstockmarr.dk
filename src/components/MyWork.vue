<template>
    <div class="my-work">
        <Overlay :show ="expanded" v-on:close="close">
            <div class="work-navigation left" :class="{hidden: !expanded}" @click="previous"></div>
            <div class="work-navigation right" :class="{hidden: !expanded}" @click="next"></div>
        </Overlay>
        <Wrapper :width="'1000px'" :class="{hidden: !toggle}">
            <div class="content">
                <h1>My Work</h1>
                <div class="projects">
                    <div class="project" v-bind:key="project.id" v-for="project in projects">
                        <Project :name="project.name" :title="project.title" :image="project.image" :banner="project.banner" :description="project.description" :expanded="selectedId == project.id" v-on:expand="expand(project.id)" v-on:close="close"/>
                    </div>
                </div>
            </div>
        </Wrapper>
    </div>
</template>



<script>
import Project from "./Project"
import Wrapper from "./Wrapper"
import Overlay from "./Overlay";

export default {
    name: 'MyWork',
    components: {
    Project,
    Wrapper,
    Overlay
    },
    data() {
        return {
            toggle: false,
            expanded: false,
            selectedId: 0,
            projects: [{
                id: 1,
                name: 'Master Thesis',
                title: 'Master Thesis in Cloud Technologies',
                image: `my-work/thesis.png`,
                banner: `my-work/Dashboards.png`,
                description: 'In the field of Cloud Computing, there is a large number of tools that allow companies to monitor their distributed applications. However, it can be a challenge for companies with limited resources to pick the right tools for their application. My friend Muhanad Al-Karwani and I tried to solve this issue in our master thesis. We explored ways of classifying cloud native monitoring tools that reflect their functionality, use cases and data models. The classification model was integrated into an interactive tool that we developed. The tool allows stakeholders to go through a step-by-step wizard and get recommendations for which monitoring tools to use, and how to set them up. In our work we touched upon many different cloud technologies, like Docker, Kubernetes, Azure, as well as a number of popular monitoring tools.'
            }, {
                id: 2,
                name: 'Internship',
                title: 'Internship at Microsoft',
                image: `my-work/Microsoft-dynamics.jpeg`,
                banner: `my-work/Cloud-and-edge-microsoft.jpeg`,
                description: 'I was an intern at Microsoft for eight weeks, followed by a year as a student worker. During my time there, I was part of three different projects within the field of Supply Chain Management. I was the main developer on a .NET tool that helped other developers set up their environments and data pipelines. The tool was used by both internal and third party developers, and I worked closely together with them to set the direction of the project. I was also working on a web portal for my team, written in TypeScript with React. I was responsible for making the web page compliant with Microsoft\'s accessibility policy. Finally, I was part of a project where we developed ARM templates for Azure environments. The goal was to integrate data from warehouse IoT sensors with Microsoft Dynamics, using Azure resources like Stream Analytics.'
            }, {
                id: 3,
                name: 'Bachelor Project',
                title: 'Bachelor Project in Time Series Analysis',
                image: `my-work/Bachelor.png`,
                banner: `my-work/seas-nve.jpeg`,
                description: 'I wrote my bachelor project with two friends in collaboration with SEAS-NVE, a danish electricity and heat distributor. The goal of the project was to analyze the heat consumption for a number of houses, and to try to visualize the results in a way that would be useful to the consumer. SEAS-NVE has already implemented such a tool for electricity consumption, and it has been statistically proved to work. Our work was mostly based on statistical models and time series analysis.'
            }, {
                id: 4,
                name: 'Student Job',
                title: 'Student Job at Developyn',
                image: `my-work/Developyn.png`,
                banner: `my-work/Flight-Tower.png`,
                description: 'This summer I spent five weeks at Developyn as an intern. Developyn provides web solutions and SEO for small to medium sized companies. One of their ongoing projects is an internal page for IKEA, called Flight Tower. It was my task to create a testing bot for the site, that could be used to detect errors on the site before deployment. I did this using JavaScript Selenium. During my stay, I also made a number of back end and front end projects used for training. Some of these are displayed on my GitHub, which can be found at the bottom of the site.'
            }, {
                id: 5,
                name: 'Student Job',
                title: 'Student Job at SEGES',
                image: `my-work/Seges_logo.jpg`,
                banner: `my-work/Codeception.png`,
                description: 'From 2018 to 2020 I worked at SEGES, who provides research and other services for danish pig breeders. I worked in the department of Breeding and Genetics, as student assistant in IT. My tasks included setting up new Linux servers, managing automatic mail services, and setting up test suites for their website. I created these test suites using the Codeception framework in PHP, running headless browsers with Selenium.'
            }]
        }
    },
    mounted() {
        let options = { threshold: 0.5};
        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    this.toggle = true;
                }
            })
        }, options);
        const element = this.$el.querySelector(".projects").firstChild;
        observer.observe(element);
    },
    methods: {
        expand(id) {
            this.expanded = true;
            this.selectedId = id;
        },
        close() {
            this.expanded = false;
            this.selectedId = 0;
        },
        next() {
            if (this.selectedId < this.projects.length)
            {
                this.selectedId++;
            }
            else {
                this.selectedId = 1;
            }
        },
        previous() {
            if (this.selectedId > 1)
            {
                this.selectedId--;
            }
            else {
                this.selectedId = this.projects[this.projects.length - 1].id;
            }
        }
    }
}
</script>

<style scoped>
@import "../colors.css";


.my-work {
    background-color: var(--col1);
}

.content {
    box-sizing: border-box;
    padding: 60px 15px 100px;
    width: 100%;
}

h1 {
    font-size: 32px;
    text-align: center;
    line-height: 50px;
    text-transform: uppercase;
}

.project {
    width: min(calc(100vw - 30px), 300px);
    height: min(calc(100vw - 30px), 300px);
}

.projects {
    padding: 15px calc((100vw - 330px) / 2);
    display: -ms-grid;
    display: grid;
    -ms-grid-columns: 1fr;
    grid-template-columns: 1fr;
    grid-gap: 30px;
    }

.work-navigation {
    display: none;
}

@media only screen and (min-width: 680px) {

    .projects {
        padding: 15px calc((100vw - 680px) / 2);
        display: -ms-grid;
        display: grid;
        -ms-grid-columns: 1fr 35px 1fr;
        grid-template-columns: 1fr 1fr;
        grid-gap: 35px;
    }

    h1 {
        -webkit-transition: all 0.5s ease;
        -moz-transition: all 0.5s ease;
        -o-transition: all 0.5s ease;
        transition: all 0.5s ease;
    }

    .hidden h1 {
        -moz-transform: translateX(-200px);
        -webkit-transform: translateX(-200px);
            -ms-transform: translateX(-200px);
                transform: translateX(-200px);
        opacity: 0;
    }
    :nth-child(1) { --nth-child: 1}
    :nth-child(2) { --nth-child: 2}
    :nth-child(3) { --nth-child: 3}
    :nth-child(4) { --nth-child: 4}
    :nth-child(5) { --nth-child: 5}

    .project {
        transition: all 1s ease;
        -webkit-transition-delay: calc(var(--nth-child) * 1s);
        -moz-transition-delay: calc(var(--nth-child) * 1s);
        -o-transition-delay: calc(var(--nth-child) * 0.1s);
        transition-delay: calc(var(--nth-child) * 0.3s + 0.1s);
    }

    .hidden .project {
        opacity: 0;
        transform: translateY(100px);
        -moz-transform: translateY(100px);
        -o-transform: translateY(100px);
        -webkit-transform: translateY(100px);
    }
}

@media only screen and (min-width: 1000px) {

    .projects {
        padding: 15px 0;
        display: -ms-grid;
        display: grid;
        -ms-grid-columns: 1fr 35px 1fr 35px 1fr;
        grid-template-columns: 1fr 1fr 1fr;
        grid-gap: 35px;
    }

    .work-navigation {
        transition: all 0.5s;
        display: block;
        position: fixed;
        z-index: 100;
        cursor: pointer;
    }

    .work-navigation.left {
        background-image: url("../assets/navigation-icons/previous.svg");
        left: 25px;
        top: calc(50% - 50px);
        bottom: calc(50% - 50px);
        right: calc(100% - 125px);
    }

    .work-navigation.right {
        background-image: url("../assets/navigation-icons/next.svg");
        right: 25px;
        top: calc(50% - 50px);
        bottom: calc(50% - 50px);
        left: calc(100% - 125px);
    }

    .work-navigation.left:hover {
        background-image: url("../assets/navigation-icons/previous-hover.svg");
    }

    .work-navigation.left:active {
        background-image: url("../assets/navigation-icons/previous-click.svg");
    }

    .work-navigation.right:hover {
        background-image: url("../assets/navigation-icons/next-hover.svg");
    }

    .work-navigation.right:active {
        background-image: url("../assets/navigation-icons/next-click.svg");
    }

    .hidden.work-navigation.right {
        opacity: 0;
        transform: translateX(25px);
        -moz-transform: translateX(25px);
        -o-transform: translateX(25px);
        -webkit-transform: translateX(25px);
    }

    .hidden.work-navigation.left {
        opacity: 0;
        transform: translateX(-25px);
        -moz-transform: translateX(-25px);
        -o-transform: translateX(-25px);
        -webkit-transform: translateX(-25px);
    }
}


</style>
