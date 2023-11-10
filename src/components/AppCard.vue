<script>

export default {
    name: 'AppCard',
    props:{
        dateFilm: Array
    }
}
</script>

<template>
  <div>
    <p>{{ dateFilm.title }}</p>
    <p>{{ dateFilm.originalTitle }}</p>
    <p></p>
    <p></p>
    {{ dateFilm }}
  </div>
  
</template>

<style scoped lang="scss">

</style>