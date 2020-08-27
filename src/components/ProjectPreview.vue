<template>
    <div class="project-preview">
        <div class="small-screen preview" :class="{expanded: this.expanded}" :style="{ backgroundImage: 'url(' + require(`@/assets/${this.image}`) + ')' }" @mouseover="expanded=true" @mouseleave="expanded=false">
            <div class="banner">
                <div class="name">
                    <h1>{{name}}</h1>
                </div>
                <button class="expand-btn" @click="expand">Read more</button>
            </div>
        </div>
        <div class="big-screen preview" :style="{ backgroundImage: 'url(' + require(`@/assets/${this.image}`) + ')' }" @click.stop="expand">
            <div class="banner">
                <div class="name">
                    <h1>{{name}}</h1>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProjectPreview',
    props: ['image', 'name'],
    methods: {
        expand() {
            this.$emit('expand');
        },
        close() {
            this.$emit('close');
        }
    },
    data() {
        return {
            expanded: false
        }
    }
}
</script>

<style scoped>
@import "../colors.css";

.project-preview {
    width: 100%;
    height: 100%;
}

.big-screen {
    display: none;
}

.preview {
    box-sizing: border-box;
    position: relative;
    width: 100%;
    height: 100%;
    background-color: white;
    background-repeat: no-repeat;  
    background-size: 100% 100%;
    background-position: center center;
    border: 1px solid #222;
}

.banner {
    box-sizing: border-box;
    position: absolute;
    background-color: var(--col5);
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


.expanded .banner {
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
    color: white;
    font-size: 18px;
    background: var(--col4);
    padding: 5px 10px;
    border-radius: 5px;
}

.expand-btn:hover {
    background-color: blue;
}

@media only screen and (min-width: 1000px) {

    .preview:hover .banner {
        opacity: 1;
        max-width: 100%;
        padding-left: 20px;
        padding-right: 40px;
    }

    .small-screen {
        display: none;
    }

    .big-screen {
        display: block;
        cursor: pointer;
    }

    .banner {
        height: 65px;
    }
}


</style>
