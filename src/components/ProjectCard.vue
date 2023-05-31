<script>
import {store} from '../store.js';

export default {
  data() {
    return{

      store,

      baseUrl: 'http://127.0.0.1:8000/',

      viewBtn: false,
    }

  },

  props: {

    project: Object,
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
    
    <div class="card" @mouseover="viewBtn = true" @mouseleave="viewBtn = false">
      <img :src="image" class="card-img-top" alt="project-image">
      <div class="card-body">
        <h5 class="title" :class="this.store.activeIndex == 0 ? 'text_0' : '', this.store.activeIndex == 1 ? 'text_1' : '', this.store.activeIndex == 2 ? 'text_2' : ''">{{ project.title }}</h5>
        <div class="type">({{ project.type ? project.type.name : 'Tipo indefinito' }})</div>
        <span class="techs pe-2" :style="{color:  tech.color }" v-for="tech in project.technologies"> {{ tech.name }} </span>

        <div v-show="viewBtn" class="btn-container">
          <button class="btn" :class="this.store.activeIndex == 0 ? 'btn-outline-danger' : '', this.store.activeIndex == 1 ? 'btn-outline-primary' : '', this.store.activeIndex == 2 ? 'btn-outline-secondary' : ''">
            <router-link class="router-link" :to="{name: 'projects.show', params: {slug: project.slug}}" >ESPLORA</router-link>
          </button>
        </div>
      </div>
    </div>

</template>

<style scoped lang="scss">

.card{
  width: calc(100% / 3 - 50px);
  
  transition: all .2s ease-in-out;
  
  img{
      height: 200px;
  }
  
  .card-body{
  
    .title{
      font-size: 1.6em;
      font-family: 'Bruno Ace', cursive;

      margin-bottom: 0;
    }
  
    .type{
      padding-bottom: 26px;
      
      color: white;
      font-size: 0.9em;
      font-family: 'Bruno Ace', cursive;
    }

    .techs{
      font-family: 'Bruno Ace', cursive;
    }
  }
  .btn-container{
    position: relative;

    display: flex;
    justify-content: flex-end;

    width: 100%;

    .btn{
      font-family: 'Bruno Ace', cursive;
    }
  }
  
  &:hover{
    transform: scale(1.2);

    z-index: 3;
  }

  &:hover .btn-container{
    position: absolute;
    bottom: 0px;
    right: 0px;
  }
}


</style>
