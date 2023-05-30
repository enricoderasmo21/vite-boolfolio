<script>
import axios from 'axios';

import ProjectCard from './ProjectCard.vue';

export default {
  data() {
    return{

      projects: [],
      
    }
  },

  components: {

    ProjectCard,
  
  },

  created() {
    
    this.getProjects();
    },
    
    methods: {
    
    getProjects() {
    
      axios.get('http://127.0.0.1:8000/api/projects').then(response => {
    
        this.projects = response.data.results;
        
      });
    },
      
  },
}

</script>

<template>

  <h2 class="text-center">I miei progetti</h2>

  <div class="cards-container">

    <ProjectCard v-for="project in projects"  :project="project"></ProjectCard>

  </div>
 
</template>

<style scoped lang="scss">
.cards-container{
  display: flex;
  flex-flow: row wrap;
  gap: 30px;

  margin: 0 auto;

  width: 80%;
}

</style>
