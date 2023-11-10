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
    <div>
        <h1>Boolflix</h1>

        <input @keyup.enter="search" type="text" v-model="this.store.searchVal">
        <button @click="search">Cerca</button>
    </div>
</template>

<style scoped lang="scss"></style>