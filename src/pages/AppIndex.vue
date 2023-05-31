<script>
import axios from 'axios';
import {store} from '../store.js';

import ProjectCard from '../components/ProjectCard.vue';

export default {

  name: 'AppIndex',

  data() {
    return{

      store,

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

  <div class="background">

    <h2 class="text-center title">I miei progetti</h2>
  
    <div class="cards-container">
  
      <ProjectCard v-for="project in projects"  :project="project"></ProjectCard>
  
    </div>

  </div>

 
</template>

<style scoped lang="scss">

.background{
  margin-top: 100px;
  padding-bottom: 80px;

  background-color: black;

  .title{
    padding-top: 30px;
    padding-bottom: 50px;

    color: white;
    font-size: 3.6em;
    font-family: 'Bruno Ace', cursive;
  }
  .cards-container{
    display: flex;
    flex-flow: row wrap;
    gap: 50px;
  
    margin: 0 auto;
  
    width: 90%;
  }

}


</style>
