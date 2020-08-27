<template>
  <div class="transition">
    <div class="top-layer" :class="{active: toggle}"></div>
    <div class="top-layer top-layer--2" :class="{active: toggle}"></div>
    <div class="top-layer top-layer--3" :class="{active: toggle}"></div>
    <div class="top-layer top-layer--4" :class="{active: toggle}"></div>
    <div class="top-layer top-layer--5" :class="{active: toggle}"></div>
  </div>
</template>

<script>
export default {
    name: 'Transition',
    props: ["toggle"]
}
</script>

<style>
@import "../colors.css";


.top-layer {
	position: absolute;
	width: 100%;
	height: 100%;
	top: -100%;
	left: 0;
	bottom: auto;
	right: auto;
	background: var(--col1);
    -moz-transition: all 0.9s cubic-bezier(0.6, 0.05, 0.4, 1);
    -webkit-transition: all 0.9s cubic-bezier(0.6, 0.05, 0.4, 1);
    -o-transition: all 0.9s cubic-bezier(0.6, 0.05, 0.4, 1);
    transition: all 0.9s cubic-bezier(0.6, 0.05, 0.4, 1);
    z-index: 10;
}
.active {
    top: 100%;
} 
.top-layer--2 {
	background: var(--col2);
	-moz-transition-delay: 0.1s;
	-webkit-transition-delay: 0.1s;
	-o-transition-delay: 0.1s;
	transition-delay: 0.1s;
}
.top-layer--3 {
	background: var(--col3);
	-moz-transition-delay: 0.2s;
	-webkit-transition-delay: 0.2s;
	-o-transition-delay: 0.2s;
	transition-delay: 0.2s;
}
.top-layer--4 {
	background: var(--col4);
	-moz-transition-delay: 0.4s;
	-webkit-transition-delay: 0.4s;
	-o-transition-delay: 0.4s;
	transition-delay: 0.4s;
}
.top-layer--5 {
	background: var(--col5);
	-moz-transition-delay: 0.6s;
	-webkit-transition-delay: 0.6s;
	-o-transition-delay: 0.6s;
	transition-delay: 0.6s;
}
</style>