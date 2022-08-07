<template>
  <div class="header">
    <div class="blank"></div>
    <div class="bar">
        <nav @mouseover="expanded=true" @mouseleave="expanded=false">
          <div class="dropdown-icon" :class="{selected: expanded}">
            <ViewSequential :width="`100%`" :height="`100%`"/>
          </div>
          <ul :class="{expanded: expanded}">
            <li @click="goToFront()">Front</li>
            <li @click="scrollTo(`.about-me`)">About me</li>
            <li @click="scrollTo(`.my-work`)">My Work</li>
            <li @click="scrollTo(`.contact`)">Contact</li>
          </ul>
        </nav>
      <Wrapper :width="'1000px'">
        <ul class="navbar">
          <li @click="goToFront()">Front</li>
          <li @click="scrollTo(`.about-me`)">About me</li>
          <li @click="scrollTo(`.my-work`)">My Work</li>
          <li @click="scrollTo(`.contact`)">Contact</li>
        </ul>
      </Wrapper>
    </div>
  </div>
</template>

<script>
import ViewSequential from 'mdi-vue/ViewSequential.vue'
import Wrapper from "./Wrapper"

export default {
name: 'Header',
components: {
  ViewSequential,
  Wrapper
},
data() {
  return {
    expanded: false
  }
},
methods: {
  scrollTo(el) {
    this.$emit("scrollTo",el);
    this.expanded = false;
  },
  goToFront() {
    this.$emit("goToFront");
  }
}
}
</script>

<style scoped>
@import "../colors.css";


.blank {
  margin-top: 50px;
}

.bar {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  height: 50px;
  background-color: var(--col4);
  z-index: 5;
}

.navbar {
  display: none;
}


.dropdown-icon {
  box-sizing: border-box;
  float: right;
  color: var(--col2);
  height: 50px;
  width: 50px;
  padding: 5px;
}

nav ul {
  position: absolute;
  background-color: var(--col3);
  top: 50px;
  left: 0;
  right: 0;
  height: 0;
  overflow: hidden;
  white-space: nowrap;
  transition: all 0.5s ease-in-out;
}

nav ul li {
  text-transform: uppercase;
  padding: 12px 20px;
  font-size: 16px;
}

nav ul li:hover {
  background-color: var(--col5);
}

.expanded {
  height: 200px;
}

.selected {
  color: var(--col5);
}


@media only screen and (min-width: 1000px) {

  nav {
    display: none;
  }  

  .navbar {
    display: block;
  }

  .navbar li {
    text-transform: uppercase;
    float: left;
    line-height: 50px;
    color: var(--col2);
    margin: 0 10px;
    list-style-type: none;
  }

  .navbar li:hover {
    cursor: pointer;
    color: var(--col5);
  }
}

</style>
