<script>
import {store} from '../store.js';

export default {
  data() {
    return{
        
        store,

        logos: ['/img/BoolfolioLogo.png', '/img/BoolfolioLogo-2.png', '/img/BoolfolioLogo-3.png'],
    }

  },

  methods: {

    activeHome(){

        if(this.$route.name == 'home' && this.store.activeIndex == 0){

            return 'active_0';

        }
        
        if(this.$route.name == 'home' && this.store.activeIndex == 1){

            return 'active_1';
            
        }
        
        if(this.$route.name == 'home' && this.store.activeIndex == 2){

            return 'active_2';
        }
    },

    activeProject(){
        
        if(this.$route.name == 'projects.index' && this.store.activeIndex == 0){
            
            return 'active_0';
        }
            
        
        if(this.$route.name == 'projects.index' && this.store.activeIndex == 1){
            
            return 'active_1';
        }
    
        if(this.$route.name == 'projects.index' && this.store.activeIndex == 2){
        
            return 'active_2';
        }
    }
  }
}

</script>

<template>

    <header>

        <div class="navbar" :class="this.store.activeIndex == 0 ? 'nav_0' : '', this.store.activeIndex == 1 ? 'nav_1' : '', this.store.activeIndex == 2 ? 'nav_2' : ''">

            <div class="inner-left">
                <div id="logo-container">
                    <router-link :to="{name: 'home'}"> 
                        <img :src="logos[this.store.activeIndex]" alt="">
                    </router-link>
                </div>
            </div>

            <div class="inner-right">
                <div class="link-container">
                    <ul>
                        <li>
                            <router-link class="router-link link" :class="activeHome()" :to="{name: 'home'}">
                                Home
                            </router-link>
                        </li>
                        <li>
                            <router-link class="router-link link" :class="activeProject()" :to="{name: 'projects.index'}">
                                Progetti
                            </router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </div>

    </header>

</template>

<style scoped lang="scss">

.navbar{
    position: fixed;
    top: 0;
    left: 0;
    z-index: 5;

    padding: 20px 40px;

    height: 100px;
    width: 100%;

    background-color: black;

    box-shadow: 10px 20px 30px rgba($color: #000000, $alpha: 0.8);

    .inner-left{

        #logo-container{
            width: 300px;

            img{
                width: 100%;
            }
        }
    }

    .inner-right{
        display: flex;
        align-items: center;

        .link-container{
            display: flex;
            align-items: center;

            ul{
                display: flex;
                flex-direction: row;
                align-items: center;
                gap: 30px;

                .link{
                    font-family: 'Ubuntu', sans-serif;
                    color: white;
                }
            }
        }
    }
}

</style>