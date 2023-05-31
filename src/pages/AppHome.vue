<script>
import {store} from '../store.js';

export default {

    name: 'AppHome',
    
  data() {
    return{

      images: ['/img/logo_1.png', '/img/logo_2.png', '/img/logo_3.png'],

      store, 
    }

  },

  methods: {

    nextImage() {
      
      if (this.store.activeIndex >= this.images.length - 1) {
      
          this.store.activeIndex = 0;
      
      } else {
      
          this.store.activeIndex++;
      };
    },
      
    prevImage() {
      
      if (this.store.activeIndex <= 0) {
      
          this.store.activeIndex = this.images.length - 1;
      
      } else {
      
          this.store.activeIndex--;
      };
      
    },

  }

}

</script>

<template>

  <div id="home">

    <div class="_container">
      
      <div class="left-inner">
        <div id="first-sec">
          <div id="hello">
            Hello
          </div>
          <div id="_row"></div>
        </div>
        <div id="name">
          I am Enrico D'Erasmo
        </div>
        <div id="grade">
          Junior Web Developer
        </div>
        <button class="btn mt-5" :class="this.store.activeIndex == 0 ? 'btn-outline-danger' : '', this.store.activeIndex == 1 ? 'btn-outline-primary' : '', this.store.activeIndex == 2 ? 'btn-outline-secondary' : ''">
          <router-link class="router-link" :to="{name: 'projects.index'}">PROJECTS</router-link> 
        </button>
      </div>
      
      <div class="right-inner">
        
        <div id="img-container">
          <img :src="images[this.store.activeIndex]" alt="">
        </div>
        <div class="arrow-container">
          <div class="arrow" @click="prevImage()"><i class="fa-solid fa-chevron-left"></i></div>
          <div>Change theme</div>
          <div class="arrow" @click="nextImage()"><i class="fa-solid fa-chevron-right"></i></div>
        </div>
      </div>
    </div>

  </div>


</template>

<style scoped lang="scss">

#home{
  margin-top: 100px;
  padding-top:80px;

  height: calc(100vh - 100px);

  background-color: black;

  ._container{
      margin: 0px auto;
      padding: 50px 0;

      width: 80%;

      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: center;

      color: white;
      font-family: 'Bruno Ace', cursive;

      .left-inner{

          #first-sec{
              display: flex;
              flex-direction: row;
              align-items: center;
              gap: 20px;

              #hello{
                  font-size: 2.4em;
              }
              #_row{
                  height: 2px;
                  width: 500px;

                  background-color: white;

                  border-radius: 20px;
              }
          }

          #name{
              font-size: 3.4em;
          }

          #grade{
              font-size: 1.6em;
          }
      }

      .right-inner{

          #img-container{
              height: 400px;

              img{
                  height: 100%;
              }
          }

          .arrow-container{
            display: flex;
            justify-content: space-between;
            align-items: center;

            margin-top: 8px;

            .arrow{
              font-size: 2em;

              cursor: pointer;
            }
          }
        }
      }
    }

</style>