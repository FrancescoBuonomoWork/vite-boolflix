<script>
import { store } from '../store';
export default {
    name: 'HeaderApp',
    emits: ['performSearch'],
    data() {
        return {
            store
        }
    },
    methods : {
        search() {
            this.$emit('performSearch',this.store.searchVal);
            // console.log(this.store.searchVal);
            
        }
    }
}
</script>

<template>
    <header class="header">
        <h1>Boolflix</h1>

        <div class="search-wrapper">
            <input @keyup.enter="search" type="text" v-model.trim="this.store.searchVal">
            <button @click="search" >Cerca</button>
        </div>
    </header>
</template>

<style scoped lang="scss">

    .header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: black;
        color: red;
        padding: 30px 16px;
    }
</style>