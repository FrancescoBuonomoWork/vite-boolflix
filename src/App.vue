<script>
import HeaderApp from './components/HeaderApp.vue';
import MainApp from './components/MainApp.vue';

import { store } from './store';
import axios from 'axios';

export default {
  components:{
    HeaderApp,
    MainApp
  },
  data(){
    return{
      store
    }
  }
}
</script>

<template>
  <div>
    
  </div>
  
</template>

<style lang="scss">
@use './styles/general.scss';
</style>
