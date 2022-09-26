<template>
    <div class="project">
        <ProjectPreview :name="name" :image="image" v-on:expand="expand"/>
        <button class="close-btn" :class="{hidden: !expanded}" @click="close">Close</button>
        <div class="content" :class="{hidden: !expanded}">
            <div class="top-image" :style="{ backgroundImage: 'url(' + require(`@/assets/${this.banner}`) + ')' }"></div>
            <div class="project-description">
                <h1>{{name}}</h1>
                <p>{{description}}</p>
            </div>
        </div>
    </div>
</template>

<script>
import ProjectPreview from "./ProjectPreview"

export default {
    name: 'Project',
    props: ['name', 'image', 'banner', 'description', 'expanded'],
    components: {
        ProjectPreview
    },
    methods: {
        expand() {
            this.$emit('expand');
        },
        close() {
            this.$emit('close');
        }
    }
}
</script>

<style scoped>
@import "../colors.css";

.hidden {
    visibility: hidden;
    opacity: 0;
}

.content {
    transition: all 0.5s ease-in-out;
    -o-transition: all 0.5s ease-in-out;
    -moz-transition: all 0.5s ease-in-out;
    -webkit-transition: all 0.5s ease-in-out;

    position: fixed;
    z-index: 10;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: white;

    overflow: auto;
    height: 100%;
}


.close-btn {
    transition: all 0.5s ease-in-out;
    -o-transition: all 0.5s ease-in-out;
    -moz-transition: all 0.5s ease-in-out;
    -webkit-transition: all 0.5s ease-in-out;

    font-size: 18px;
    background-color: var(--col3);
    padding: 5px 10px;
    border-radius: 5px;
    position: fixed;
    bottom: 20px;
    right: 20px;
    height: 40px;
    width: 100px;
    z-index: 11;
}


.close-btn:hover {
    background-color: var(--col4);
}

.top-image {
    width: 100%;
    height: 30vh;
    background-repeat: no-repeat;  
    background-size: cover;
}


.project-description {
    padding: 20px 15px;
}

.project-description h1 {
    font-size: 28px;
    line-height: 40px;
}

.project-description p {
    font-size: 16px;
    line-height: 30px;
    margin: 20px 0 40px;
}


@media only screen and (min-width: 1000px) {

    .content {
        top: 100px;
        right: 150px;
        left: 150px;
        bottom: 100px;
        height: calc(100% - 200px);
    }

    .close-btn {
        display: none;
    }

    .project-description h1 {
        font-size: 36px;
    }

    .project-description p {
        font-size: 24px;
        line-height: 38px;
    }
}

</style>
