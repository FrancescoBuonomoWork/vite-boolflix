<script>

export default {
    name: 'AppCard',
    props: {
        item: Object,
        required: true
    },
    data() {
        return {

            languages: ['it', 'en', 'es']
        }
    },
    methods: {
        getTitleOrName(){
            if(this.item.title) {
                return this.item.title
            } else {
                return this.item.name
            }
        },
        getTitleOrNameOriginal(){
            if(this.item.original_title) {
                return this.item.original_title
            } else {
                return this.item.original_name
            }
        },
        getVoteStars(vote) {
            vote = Math.ceil(vote / 2);

           
        }

    }
}
</script>

<template>
    <div class="card">
        <img :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`">
        <p>{{getTitleOrName()}}</p>
        <p>{{ getTitleOrNameOriginal() }}</p>
        <!-- <p>{{ item.title }}</p> -->
        <!-- <p>{{ item.name }}</p> -->
        <!-- <p>{{ item.original_title }}</p>
        <p>{{ item.original_name }}</p> -->
        <p>
            <img v-if="languages.includes(item.original_language)" class="flag"
                :src="`../../public/${item.original_language}.png`">
            <span v-else>{{ item.original_language }}</span>
        </p>
        <p>{{ item.vote_average }}
            <div class="star-wrapper">
                <font-awesome-icon :icon="['fas', 'star']" />
                <font-awesome-icon :icon="['fas', 'star']" />
                <font-awesome-icon :icon="['fas', 'star']" />
                <font-awesome-icon :icon="['fas', 'star']" />
                <font-awesome-icon :icon="['far', 'star']" />
            </div>
        </p>

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