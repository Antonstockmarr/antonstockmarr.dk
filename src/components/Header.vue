<template>
  <div class="header">
    <div class="blank"></div>
    <div class="bar">
      <nav @mouseover="expanded=true" @mouseleave="expanded=false">
        <div class="dropdown-icon">
          <ViewSequential :width="`100%`" :height="`100%`"/>
        </div>
        <ul :class="{expanded: expanded}">
          <li @click="goToFront()">Front</li>
          <li @click="scrollTo(`.about`)">Home</li>
          <li @click="scrollTo(`.my-work`)">My Work</li>
          <li @click="scrollTo(`.background`)">About Me</li>
          <li @click="scrollTo(`.contact`)">Contact</li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
import ViewSequential from 'mdi-vue/ViewSequential.vue'

export default {
name: 'Header',
components: {
  ViewSequential
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

.blank {
  margin-top: 50px;
}

.bar {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  height: 50px;
  background-color: darkblue;
  z-index: 5;
}

.title {
  line-height: 50px;
  float: left;
}


.dropdown-icon {
  box-sizing: border-box;
  float: right;
  color: white;
  height: 50px;
  width: 50px;
  padding: 5px;
}

nav ul {
  position: absolute;
  background-color: lightgrey;
  top: 50px;
  left: 0;
  right: 0;
  height: 0;
  overflow: hidden;
  white-space:nowrap;
  transition: all 0.5s ease-in-out;
}

nav ul li {
  text-transform: uppercase;
  padding: 12px 20px;
  font-size: 16px;
}

nav ul li:hover {
  background-color: lightgreen;
}

.expanded {
  height: 200px;
}
</style>
