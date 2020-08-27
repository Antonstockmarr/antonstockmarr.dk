<template>
    <div class="overlay">
        <div class="dark-background" :class="{hidden: !show}" @click="close"></div>
        <div class="content" :class="{hidden: !show, visible: show}">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Overlay',
    props: ['show'],
    methods: {
        close() {
            this.$emit('close');
        }
    }
}
</script>

<style scoped>

.content {
    position: fixed;
    z-index: 10;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    transition: all 0.5s ease-in-out;
    background-color: white;
}


.hidden {
    visibility: hidden;
    opacity: 0;
}

.hidden.content {
    transform: scale(0.5);
}

@media only screen and (min-width: 1000px) {
    
    .dark-background {
        position: fixed;
        z-index: 9;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        transition: all 0.5s ease-in-out;
        background-color: black;
        opacity: 0.8;
    }

    .dark-background.hidden {
        opacity: 0;
    }

    .content {
        left: calc(50% - 250px);
        width: 500px;
    }
}

  
</style>
