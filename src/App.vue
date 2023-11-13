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

      if(this.store.searchVal === '') {
        store.movies = [];
        store.serieTV = [];
      }
      // qui chiamo l api dandogli la chiave e il valore nel input del header per i film
      axios.get('https://api.themoviedb.org/3/search/movie',{
        params: {
          'api_key': this.store.apiKey,
          'query' : this.store.searchVal
        }
      }).then((res) =>{
        console.log(res.data.results)
        this.store.movies = res.data.results;

      })
      // this.store.searchVal = '';
      // qui chiamo l API per le serie tv
      axios.get('https://api.themoviedb.org/3/search/tv',{
        params: {
          'api_key': this.store.apiKey,
          'query' : this.store.searchVal
        }
      }).then((res) =>{
        console.log(res.data.results)
        this.store.series = res.data.results;

      })
      this.store.searchVal = '';
    }
  },
 
}
</script>

<template>
  <div>
    <HeaderApp @perform-search="searchApi"/>
    <MainApp/>
  </div>
  
</template>

<style lang="scss">
@use './styles/general.scss';

</style>
