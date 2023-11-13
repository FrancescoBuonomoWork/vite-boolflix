<script>

export default {
    name: 'AppCard',
    props: {
        film: Object
    },
    data() {
        return {
           
            languages:['it','en','es']
        }
    },
    methods: {
    }
}
</script>

<template>
    <div class="card">
        <p>{{ film.title }}</p>
        <p>{{ film.original_title }}</p>

        <p>
            <img v-if="languages.includes(film.original_language)"  class="flag"  :src="`../../public/${film.original_language}.png`">
            <span v-else>{{ film.original_language }}</span>    
            <!-- <img class="flag" src="../../public/Flag_of_the_United_Kingdom.svg.png">
            <img class="flag" src="../../public/Flag_of_Spain.svg.png"> -->

        </p>
        <p>{{ film.vote_average }}</p>

    </div>
</template>

<style scoped lang="scss">
.card {
    padding: 10px 5px;

    .flag {
        width: 24px;
        height: 16px;
       
    }
    
}
</style>