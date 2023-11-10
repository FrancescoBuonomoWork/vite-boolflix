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
  },
  methods:{
    searchApi(){
      console.log(this.store.searchVal)
      // qui chiamo l api dandogli la chiave e il valore nel input del header 
      axios.get('https://api.themoviedb.org/3/search/movie',{
        params: {
          'api_key': this.store.apiKey,
          'query' : this.store.searchVal
        }
      }).then((res) =>{
        console.log(res.data.results)
        this.store.movies.push(res.data.results)

      })
      this.store.searchVal = '';
    }
  },
  
}
</script>

<template>
  <div class="container">
    <HeaderApp @perform-search="searchApi"/>
    
  </div>
  
</template>

<style lang="scss">
@use './styles/general.scss';
.container{
  max-width: 1000px;
  margin: 0 auto;
}
</style>
