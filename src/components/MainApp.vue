<script>
import AppCard from './AppCard.vue';
import { store } from '../store';
export default {
    name: 'MainApp',
    components:{
        AppCard
    },
    data(){
        return{
            store
        }
    },

}
</script>

<template>
  <div>
   <h3>I Film trovati sono :</h3>
    <AppCard v-for="movie in store.movies" :film="movie" :id="movie.id"/>
    <!-- {{ this.store.movies }} -->
  </div>
  
</template>

<style scoped lang="scss">

</style>