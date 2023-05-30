<script>

export default {
  data() {
    return{

        baseUrl: 'http://127.0.0.1:8000/',
      
    }

  },

  props: {

    project: Object,
  },

  computed: {

    shortContent() {

        if(this.project.description.length > 50) {

            return this.project.description.substring(0, 50) + '...';
        } else {

            return this.project.description
        }
    },

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
    
    <div class="card">
      <img :src="image" class="card-img-top" alt="project-image">
      <div class="card-body">
        <h5 class="card-title">{{ project.title }}</h5>
        <div>{{ project.type ? project.type.name : 'Tipo indefinito' }}</div>
        <span class="pe-2" v-for="tech in project.technologies"> {{ tech.name }} </span>
        <p class="card-text">{{ shortContent }}</p>
      </div>
    </div>

</template>

<style scoped lang="scss">

.card{
    width: calc(100% / 3 - 30px);

    img{

        height: 200px;
    }
}

</style>
