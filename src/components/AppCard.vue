<script>

export default {
    name: 'AppCard',
    props:{
        film: Object
    }
}
</script>

<template>
    
  <div class="card">
    <p>{{ film.title }}</p>
    <p>{{ film.original_title }}</p>
    <p>{{ film.original_language }}</p>
    <p>{{ film.vote_average }}</p>

  </div>
  
</template>

<style scoped lang="scss">
.card{
    padding: 10px 5px;
}
</style>