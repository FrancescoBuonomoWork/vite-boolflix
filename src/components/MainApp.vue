<script>
import AppCard from './AppCard.vue';
import { store } from '../store';
export default {
    name: 'MainApp',
    components: {
        AppCard
    },
    data() {
        return {
            store
        }
    },


}
</script>

<template>
    <main class="main">
        <div v-if="store.movies.length > 0">
            <h3>I Film trovati sono :</h3>
            <AppCard v-for="movie in store.movies" :item="movie" 
            :id="movie.id" />
        </div>
        <div v-else>Nessun film trovato</div>
        <!-- {{ this.store.movies }} -->
        <div v-if="store.series.length > 0">
            <h3>Le Serie TV trovate sono:</h3>
            <AppCard v-for="serie in store.series" 
            :item="serie" 
            :id="serie.id"/>
        </div>
        <div v-else>Nessun Serie trovata</div>

    </main>
</template>

<style scoped lang="scss">
.main{
    background-color: gray;
    flex-grow: 1;
    overflow-y: auto;
}


</style>