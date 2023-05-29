<script>
import axios from 'axios';

export default {
  data() {
    return{

      projects: [],
      
    }
  },

  components: {
  
  },

  created() {
    
    this.getProjects();
    },
    
    methods: {
    
    getProjects() {
    
      axios.get('http://127.0.0.1:8000/api/projects').then(response => {
    
        this.projects = response.data.results;
        
      });
    }
      
  },
}

</script>

<template>

  <h2 class="text-center">I miei progetti</h2>

  <div class="cards-container" >

    <div class="card" v-for="project in projects">
      <!-- <img src="..." class="card-img-top" alt="..."> -->
      <div class="card-body">
        <h5 class="card-title">{{project.title}}</h5>
        <p class="card-text">{{ project.description }}</p>
      </div>

    </div>

  </div>
 
</template>

<style scoped lang="scss">
.cards-container{
  display: flex;
  flex-flow: row wrap;
  gap: 30px;

  margin: 0 auto;

  width: 80%;

  .card{
    width: calc(100% / 4 - 30px) ;
  }
}

</style>
