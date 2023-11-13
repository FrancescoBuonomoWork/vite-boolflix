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
        <div class="container">
            <div class="row">
                <div class="col">
                    <div class="row" v-if="store.movies.length > 0">
                        <h3 class="col">I Film trovati sono :</h3>
                        <AppCard class="col-4" v-for="movie in store.movies" :item="movie" :id="movie.id" />
                    </div>
                    <div class="col" v-else>Nessun film trovato</div>

                </div>
                <div class="row">
                    <div class="col">

                        <div class="row" v-if="store.series.length > 0">
                            <h3 class="col">Le Serie TV trovate sono:</h3>
                            <AppCard class="col-4" v-for="serie in store.series" :item="serie" :id="serie.id" />
                        </div>
                        <div class="col" v-else>Nessun Serie trovata</div>
                    </div>
                </div>
            </div>
        </div>

    </main>
</template>

<style scoped lang="scss">
.main {
    background-color: gray;
    flex-grow: 1;
    overflow-y: auto;
    // display: flex;
    // justify-content: space-around;

}
</style>