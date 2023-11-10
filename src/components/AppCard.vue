<script>

export default {
    name: 'AppCard',
    props:{
        film: Object
    }
}
</script>

<template>
  <div>
    <p>{{ film.title }}</p>
    <p>{{ film.originalTitle }}</p>
    <p></p>
    <p></p>
    <!-- {{ dateFilm }} -->
  </div>
  
</template>

<style scoped lang="scss">

</style>