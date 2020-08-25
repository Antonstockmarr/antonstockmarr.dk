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


.top-layer {
	position: absolute;
	width: 100%;
	height: 100%;
	top: -100%;
	left: 0;
	bottom: auto;
	right: auto;
	background: #393e46;
    transition: all 0.9s cubic-bezier(0.6, 0.05, 0.4, 1);
    z-index: 10;
}
.active {
    top: 100%;
} 
.top-layer--2 {
	background: #6c567b;
	transition-delay: 0.1s;

}
.top-layer--3 {
	background: #6c5b7b;
	transition-delay: 0.2s;
}
.top-layer--4 {
	background: #c06c84;
	transition-delay: 0.4s;
}
.top-layer--5 {
	background: #f67280;
	transition-delay: 0.6s;
}

</style>