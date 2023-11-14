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
                        <h3 class="col title">I Film trovati sono :</h3>
                        <AppCard  v-for="movie in store.movies" :item="movie" :id="movie.id" />
                    </div>
                    <h3 class="col title" v-else>Nessun film trovato</h3>

                </div>
                <div class="row">
                    <div class="col">
                        <div class="row" v-if="store.series.length > 0">
                            <h3 class="col title">Le Serie TV trovate sono:</h3>
                            <AppCard v-for="serie in store.series" :item="serie" :id="serie.id" />
                        </div>
                        <h3 class="col title" v-else>Nessun Serie trovata</h3>
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
    .title{
        font-weight: 700;
        font-size: 24px;
        padding: 20px 0;
    }
}
</style>