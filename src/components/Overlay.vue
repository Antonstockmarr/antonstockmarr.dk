<template>
    <div class="overlay" :class="{visible: show, hidden: !show}">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'Overlay',
    props: ['show']
}
</script>

<style scoped>


.overlay {
    position: fixed;
    background-color: white;
    z-index: 10;
    transition: all 0.5s ease-in-out;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;

}

.visible {
    opacity: 1;
}

.hidden {
    visibility: hidden;
    opacity: 0;
    transform: scale(0.5);
  }
</style>
