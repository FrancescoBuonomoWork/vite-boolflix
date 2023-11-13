<script>

export default {
    name: 'AppCard',
    props: {
        item: Object,
        required: true
    },
    data() {
        return {
            languages: ['it', 'en', 'es'],

        }
    },
    methods: {
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
        }
    }
}
</script>

<template>
    <div class="card">
        <img :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`">
        <p>{{ getTitleOrName() }}</p>
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
        <p>
            <!-- {{ Math.ceil(item.vote_average / 2) }} -->
        <ul class="star-wrapper">
            <li v-for="star in voteScale5">
                <font-awesome-icon :icon="['fas', 'star']" />
            </li>
            <li v-for="star in 5 - voteScale5">
                <font-awesome-icon :icon="['far', 'star']" />
            </li>
        </ul>
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

    .star-wrapper {
        display: flex;
    }
}
</style>