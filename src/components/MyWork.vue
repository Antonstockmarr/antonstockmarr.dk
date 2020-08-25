<template>
  <div class="my-work">
      <h1>My Work</h1>
      <div class="project" v-bind:key="project.id" v-for="project in projects">
          <Project :name="project.name" :image="project.image" :description="project.description"/>
      </div>
  </div>
</template>



<script>
import Project from "./Project"

export default {
    name: 'MyWork',
    components: { Project },
    data() {
        return {
            projects: [{
                id: 1,
                name: 'Bachelor Project',
                image: `logo.png`,
                description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc at euismod libero, non varius lectus. Quisque convallis ligula quis metus pretium, ut mattis magna tempor. Pellentesque mattis mattis pulvinar. Pellentesque nec nisi vitae risus scelerisque feugiat. Nunc lacinia hendrerit sapien vitae ultrices. Curabitur nibh felis, facilisis non lacus quis, tincidunt consequat turpis.'
            }, {
                id: 2,
                name: 'Landbrug og fødevarer',
                image: `logo.png`,
                description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc at euismod libero, non varius lectus. Quisque convallis ligula quis metus pretium, ut mattis magna tempor. Pellentesque mattis mattis pulvinar. Pellentesque nec nisi vitae risus scelerisque feugiat. Nunc lacinia hendrerit sapien vitae ultrices. Curabitur nibh felis, facilisis non lacus quis, tincidunt consequat turpis.Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc at euismod libero, non varius lectus. Quisque convallis ligula quis metus pretium, ut mattis magna tempor. Pellentesque mattis mattis pulvinar. Pellentesque nec nisi vitae risus scelerisque feugiat. Nunc lacinia hendrerit sapien vitae ultrices. Curabitur nibh felis, facilisis non lacus quis, tincidunt consequat turpis.'
            }, {
                id: 3,
                name: 'Developyn',
                image: `logo.png`,
                description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc at euismod libero, non varius lectus. Quisque convallis ligula quis metus pretium, ut mattis magna tempor. Pellentesque mattis mattis pulvinar. Pellentesque nec nisi vitae risus scelerisque feugiat. Nunc lacinia hendrerit sapien vitae ultrices. Curabitur nibh felis, facilisis non lacus quis, tincidunt consequat turpis.Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc at euismod libero, non varius lectus. Quisque convallis ligula quis metus pretium, ut mattis magna tempor. Pellentesque mattis mattis pulvinar. Pellentesque nec nisi vitae risus scelerisque feugiat. Nunc lacinia hendrerit sapien vitae ultrices. Curabitur nibh felis, facilisis non lacus quis, tincidunt consequat turpis.'
            }]
        }
    },
}
</script>

<style scoped>

.my-work {
    box-sizing: border-box;
    padding: 30px 15px 50px;
    width: 100%;
    background-color: lightblue;
}

h1 {
    font-size: 32px;
    text-align: center;
    line-height: 50px;
}

.project {
    margin: 15px 0px;
    width: 100%;
    height: 300px;
}



</style>
