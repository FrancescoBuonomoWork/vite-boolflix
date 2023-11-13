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
    <div class="container">

        <h3>I Film trovati sono :</h3>
        <AppCard v-for="movie in store.movies" :item="movie" :id="movie.id" />
        <!-- {{ this.store.movies }} -->
        <h3>Le Serie TV trovate sono:</h3>
        <AppCard v-for="serie in store.series" :item="serie" :id="serie.id"/>


    </div>
</template>

<style scoped lang="scss"></style>