<template>
        <select v-model="valueGenre" class="form-select w-15 mb-5 my-4" aria-label="Default select example" @change="onChange">    
            <option value="All">All</option>
            <option v-for="(genre, index) in genreMusic" :key="index" :value="genre">{{genre}}</option>
            
        </select>
        
    
</template>
<script>
export default {
    name:"Selectbar",
    props: {
        genreMusic: Array,
    },
    data() {
        return {
            valueGenre :"",
            genreActive: "",
        };
    },
    methods: {
        onChange () {
            //this.$emit('genreChange', this.valueGenre);
            this.genreActive = this.valueGenre;   
            this.$emit("genreChange", this.genreActive);
        }
    },    
}
</script>
<style lang="scss" scoped>
    
</style>