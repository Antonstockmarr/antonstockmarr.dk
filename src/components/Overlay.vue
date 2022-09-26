<template>
    <div class="overlay">
        <div class="dark-background" :class="{hidden: !show}" @click="close"></div>
        <slot></slot>
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


.overlay {
    transition: all 0.5s ease-in-out;
    -o-transition: all 0.5s ease-in-out;
    -moz-transition: all 0.5s ease-in-out;
    -webkit-transition: all 0.5s ease-in-out;
}

.hidden {
    visibility: hidden;
    opacity: 0;
}

@media only screen and (min-width: 1000px) {
    
    .dark-background {
        position: fixed;
        z-index: 9;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        background-color: black;
        opacity: 0.8;
    }
    
}

  
</style>
