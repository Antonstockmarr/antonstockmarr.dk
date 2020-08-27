<template>
    <div class="wrapper" :style="cssProp">
        <slot></slot>
    </div>
</template>



<script>

export default {
    name: 'Wrapper',
    props: ["width"],
    computed: {
        cssProp() {
            return {
                '--wrapperWidth': this.width
            }
        }
    }
}

</script>

<style scoped>


@media only screen and (min-width: 1000px) {
    
    .wrapper {
        margin: 0 auto;
        width: var(--wrapperWidth);
    }
}

</style>