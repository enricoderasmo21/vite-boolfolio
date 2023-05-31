<script>
import axios from 'axios';
import {store} from '../store.js';

export default {

  name: 'AppShow',

  data() {
    return{

      store,

      project: {},

      projectSlug: '',

      baseUrl: 'http://127.0.0.1:8000/',
      
    }
  },

  mounted(){

    this.projectSlug = this.$route.params.slug;

    this.getProject();
  },

  methods: {

    getProject() {

        axios.get('http://127.0.0.1:8000/api/projects/' + this.projectSlug).then(response => {

            this.project = response.data.project;

        });
    }
  },

  computed: {
      
      image() {
      
          if(this.project.image){
      
              return this.baseUrl + 'storage/' + this.project.image;
      
          } else if(this.project.image == null) {
      
              return 'https://getuikit.com/v2/docs/images/placeholder_600x400.svg';
          }
      },
      
    },
}

</script>

<template>
    <div class="background">

        <div class="jumbo">
            <img :src="image" alt="">
        </div>

        <div class="info-container">
            <h2 class="title" :class="this.store.activeIndex == 0 ? 'text_0' : '', this.store.activeIndex == 1 ? 'text_1' : '', this.store.activeIndex == 2 ? 'text_2' : ''">
                {{ project.title }}
            </h2>
    
            <p class="text">{{ project.description }}</p>
        </div>

    </div>
</template>

<style scoped lang="scss">

.background{
    margin-top: 100px;

    background-color: black;

    .jumbo{
        width: 100%;
        height: calc(100vh - 100px) ;

        overflow: hidden;

        img{
            width: 100%;
        }
    }

    .info-container{

        padding: 50px 60px;


        .title{
            padding-bottom: 80px;
    
            text-align: center;
            font-size: 3em;
            font-family: 'Bruno Ace', cursive;
        }
    
        .text{
            font-size: 1.4em;
            font-family: 'Ubuntu', sans-serif;
            color: white;
        }
    }

}


</style>
