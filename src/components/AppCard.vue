<script>

export default {
    name: 'AppCard',
    props: {
        film: Object
    },
    data() {
        return {
            languages: [
                {
                    lang: 'it',
                    flagsSRC: "../../public/Flag_of_Italy.svg.png",
                },
                {
                    lang: 'en',
                    flagsSRC: "../../public/Flag_of_the_United_Kingdom.svg.png",
                },
                {
                    lang: 'sp',
                    flagsSRC: "../../public/Flag_of_Spain.svg.png"
                },



            ]
        }
    },
    methods: {
        // getFlag(){
        //     v-if="film.original_language === 'it'"

        // }
    }
}
</script>

<template>
    <div class="card">
        <p>{{ film.title }}</p>
        <p>{{ film.original_title }}</p>
        <p>{{ film.original_language }}
            <img v-show="film.original_language === language.lang" v-for="language in languages" class="flag" :src="language.flagsSRC">
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