<script>

export default {
    name: 'AppCard',
    props: {
        item: Object,
        required: true
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
        <p>{{ item.title }}</p>
        <p>{{ item.original_title }}</p>

        <p>
            <img v-if="languages.includes(item.original_language)"  class="flag"  :src="`../../public/${item.original_language}.png`">
            <span v-else>{{ item.original_language }}</span>    


        </p>
        <p>{{ item.vote_average }}</p>

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