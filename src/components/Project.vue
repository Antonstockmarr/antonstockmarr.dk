<template>
    <div class="project">
        <div class="preview" :style="{ backgroundImage: 'url(' + require(`@/assets/${this.image}`) + ')' }">
            <div class="banner">
                <div class="name">
                    <h1>{{name}}</h1>
                </div>
                <button class="expand-btn" @click="expand()">Read more</button>
            </div>
        </div>
        <Overlay :show ="expanded">
            <button class="close-btn" @click="close()">Close</button>
            <div class="content">
                <div class="top-image" :style="{ backgroundImage: 'url(' + require(`@/assets/${this.image}`) + ')' }"></div>
                <div class="project-description">
                    <h1>{{name}}</h1>
                    <p>{{description}}</p>
                </div>
            </div>
        </Overlay>
    </div>
</template>

<script>
import Overlay from "./Overlay"

export default {
    name: 'Project',
    props: ['name', 'image', 'description'],
    components: {
        Overlay
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



.preview {
    box-sizing: border-box;
    position: relative;
    width: 100%;
    height: 100%;
    background-color: grey;
    background-repeat: no-repeat;  
    background-size: cover;
    border: 1px solid #222;
}

.banner {
    box-sizing: border-box;
    position: absolute;
    background-color: rgba(255,182,193,0.8);
    bottom: 20px;
    height: 100px;
    padding: 10px 0;
    transition: all 0.5s ease-in-out;
    -webkit-transition: all 0.5s ease-in-out;
    -moz-transition: all 0.5s ease-in-out;
    -o-transition: all 0.5s ease-in-out;
    opacity: 0;
    max-width: 0;
    white-space:nowrap;
    overflow:hidden;
}


.preview:hover .banner {
    opacity: 1;
    max-width: 100%;
    padding-left: 20px;
    padding-right: 40px;
}

.name {
    font-size: 24px;
    line-height: 45px;
}

button {
    cursor: pointer;
}

.expand-btn {
    color: #fff;
    font-size: 18px;
    background: darkblue;
    padding: 5px 10px;
    border-radius: 5px;
}

.expand-btn:hover {
    background-color: blue;
}

.close-btn {
    font-size: 18px;
    background-color: lightblue;
    padding: 5px 10px;
    border-radius: 5px;
    position: fixed;
    bottom: 20px;
    right: 20px;
    height: 40px;
    width: 100px;
}


.close-btn:hover {
    background-color: blue;
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
    background-color: red;
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

</style>
