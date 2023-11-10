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
    <AppCard v-for="mouvie in this.store.movies" :dateFilm="this.store.movies"/>
    <!-- {{ this.store.movies }} -->
  </div>
  
</template>

<style scoped lang="scss">

</style>