<script>
import {store} from './store.js';

import AppHeader from './components/AppHeader.vue'

export default {
  data() {
    return{

      store,
      
    }

  },

  components: {

    AppHeader,
  
  }
}

</script>

<template>

  <AppHeader></AppHeader>
  <router-view></router-view>

</template>

<style scoped lang="scss">

</style>
