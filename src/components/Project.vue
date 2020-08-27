<template>
    <div class="project">
        <ProjectPreview :name="name" :image="image" v-on:expand="expand"/>
        <Overlay :show ="expanded" v-on:close="close">
            <button class="close-btn" @click="close">Close</button>
            <div class="content">
                <div class="top-image" :style="{ backgroundImage: 'url(' + require(`@/assets/${this.banner}`) + ')' }"></div>
                <div class="project-description">
                    <h1>{{name}}</h1>
                    <p>{{description}}</p>
                </div>
            </div>
        </Overlay>
    </div>
</template>

<script>
import ProjectPreview from "./ProjectPreview"
import Overlay from "./Overlay"

export default {
    name: 'Project',
    props: ['name', 'image', 'banner', 'description'],
    components: {
        Overlay,
        ProjectPreview
    },
    data() {
        return {
            expanded: false
        }
    },
    methods: {
        expand() {
            this.expanded = true;
        },
        close() {
            this.expanded = false;
        }
    }
}
</script>

<style scoped>
@import "../colors.css";


.close-btn {
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

.content {
    overflow: auto;
    height: 100%;
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
