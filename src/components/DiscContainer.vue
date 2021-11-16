<template>
    
    <div class="row row-cols-1 row-cols-md-5 g-4">
        <SelectBar :genreMusic="genreList"></SelectBar>
        <div class="col" v-for="(disc, i) in discList" :key="i">
            <CardDisc :author="disc.author" 
            :genre="disc.genre" 
            :poster="disc.poster" 
            :title="disc.title" 
            :year="disc.year">
            </CardDisc>
        </div>
    </div>
</template>
<script>
import axios from "axios";
import CardDisc from "./CardDisc.vue";
import SelectBar from "./SelectBar.vue";


export default {
    name:"DiscContainer",
    components: {CardDisc, SelectBar},
    data() {
        return {
            discList: [],
        };
    },
    computed: {
        getGenreList() {
            const genreList = [];

            this.discList.forEach((genreMusic) => {
                const {genre} = genreMusic;

                if(!genreList.includes(genre)) {
                    genreList.push(genre)
                }
            });
            console.log(genreList);
            return genreList;
        },
    },

    mounted() {
        axios.get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((resp) =>{
        //console.log(resp.data.response);
        this.discList.push(...resp.data.response)
        });
    }
}
</script>
<style lang="scss" scoped>

</style>