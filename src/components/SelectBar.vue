<template>
    <select class="form-select" aria-label="Default select example">
        <option selected>All</option>
        <option v-for="(genre, index) in genreMusic" :key="index" :value="genre[i]">{{genreMusic[i]}}</option>
       
    </select>
</template>
<script>
export default {
    name:"Selectbar",
    props: {
        genreMusic: Array,
    },
    
}
</script>
<style lang="scss" scoped>
    
</style>