<script>
import axios from 'axios'
import { store } from '../store'
export default {
    name: 'AppCard',
    props: {
        item: Object,
        required: true,
        cardType: String,
    },
    data() {
        return {
            languages: ['it', 'en', 'es'],
            store,
            cast: [],
        }
    },
    methods: {
        fetchCast() {
            //this.store.cast = [];
            let creditsUrl;
            if (this.cardType === 'MOVIE') {
                creditsUrl = `https://api.themoviedb.org/3/movie/${this.item.id}/credits`
            } else {
                creditsUrl = `https://api.themoviedb.org/3/tv/${this.item.id}/credits`
            }
            axios.get(creditsUrl, {
                params: {
                    'api_key': this.store.apiKey,
                }
            }).then((res) => {
                console.log(res.data.cast);
                this.cast = res.data.cast.slice(0, 5)
            })


            // axios.get(`https://api.themoviedb.org/3/movie/${this.item.id}/credits`,{
            //     params :{
            //         'api_key': this.store.apiKey,
            //     }
            // }).then((res)=>{
            //     console.log(res.data.cast);
            //     this.cast = res.data.cast.slice(0,5)
            // })

            // axios.get(`https://api.themoviedb.org/3/tv/${this.item.id}/credits`,{
            //     params :{
            //         'api_key': this.store.apiKey,
            //     }
            // }).then((res)=>{
            //     console.log(res.data.cast);  
            //     this.cast = res.data.cast.slice(0,5)
            // })


        },
        getTitleOrName() {
            if (this.item.title) {
                return this.item.title
            } else {
                return this.item.name
            }
        },
        getTitleOrNameOriginal() {
            if (this.item.original_title) {
                return this.item.original_title
            } else {
                return this.item.original_name
            }
        },
    },
    computed: {
        voteScale5() {
            return Math.ceil(this.item.vote_average / 2)
        },
    },
    mounted() {
        console.log('mounted', this.cast);
    },
    created() {
        console.log('created', this.cast);
    }
}
</script>

<template>
    <div class="col-4">

        <div class="card">
            <div class="card-wrapper">

                <div class="card__img-wrapper">
                    <img v-if="item.poster_path" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`">
                    <img v-else src="/carro.jpg" alt="">

                </div>
                <div class="card__description-wrapper">

                    <p>Titolo:{{ getTitleOrName() }}</p>
                    <p>Titolo originale:{{ getTitleOrNameOriginal() }}</p>
                    <p>
                        <img v-if="languages.includes(item.original_language)" class="flag"
                            :src="`../../public/${item.original_language}.png`">
                        <span v-else>{{ item.original_language }}</span>
                    </p>
                    <ul class="star-wrapper">

                        <li v-for="star in voteScale5">
                            <font-awesome-icon :icon="['fas', 'star']" />
                        </li>
                        <li v-for="star in 5 - voteScale5">
                            <font-awesome-icon :icon="['far', 'star']" />
                        </li>
                    </ul>
                    <button @click="fetchCast()">Vedi cast</button>
                    <ul>
                        <li v-for="n in cast">
                            <p>Personaggio: {{ n.character }}</p>
                            <p>Nome attore: {{ n.original_name }}</p>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.card {
    // padding: 10px 5px;


    .flag {
        width: 24px;
        height: 16px;

    }

    .star-wrapper {
        display: flex;
    }

    .card-wrapper {
        position: relative;

        .card__description-wrapper {
            display: none;
            position: absolute;
            top: 0px;
            left: 0px;
            right: 0;
            bottom: 0;
            background-color: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 10px 10px;
            line-height: 1.5em;

        }
    }

    &:hover .card__description-wrapper {
        display: block;
    }
}

.col-4 {
    padding: 10px 5px;
}</style>