<script>
import axios from 'axios'
import { store } from '../store'
export default {
    name: 'AppCard',
    props: {
        item: Object,
        required: true
    },
    data() {
        return {
            languages: ['it', 'en', 'es'],
            store,
            cast:[],

        }
    },
    methods: {
        fetchCast(){
            // this.$emit('showCast');
            axios.get(`https://api.themoviedb.org/3/movie/${this.item.id}/credits`,{
                params :{
                    'api_key': this.store.apiKey,
                    
                }
            }).then((res)=>{
                console.log(res.data.cast);
               
                this.cast = res.data.cast.slice(0,5)
            })

          
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
    }
}
</script>

<template>
    <div class="card">
        <div class="card-wrapper">

            <div class="card__img-wrapper">
                <img :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`">
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
</template>

<style scoped lang="scss">
.card {
    padding: 10px 5px;
    flex-shrink: 0;

    .flag {
        width: 24px;
        height: 16px;

    }

    .star-wrapper {
        display: flex;
    }
    .card-wrapper{
        position: relative;
        .card__description-wrapper{
            display: none;
            position: absolute;
            top: 0px;
            left: 0px;
            right: 0;
            bottom: 0;
            background-color: black;
            color: white;
            padding: 10px 10px;
            line-height: 1.5em;
           
        }
    }
    &:hover .card__description-wrapper{
        display: block;
    }
}
</style>