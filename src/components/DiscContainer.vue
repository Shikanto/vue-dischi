<template>
    <div class="container-disc">
        <h1>Seleziona il tuo genere Musicale:</h1>
        <SelectBar @genreChange="onGenreFilter" :genreMusic="getGenreList"></SelectBar>
        <div class="row row-cols-1 row-cols-md-5 g-4">
            <div class="col" v-for="(disc, i) in filteredGenreMusic" :key="i">
                <CardDisc :author="disc.author" 
                :genre="disc.genre" 
                :poster="disc.poster" 
                :title="disc.title" 
                :year="disc.year">
                </CardDisc>
            </div>
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
            genreFilter: "",
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
        filteredGenreMusic() {
            if (!this.genreFilter || this.genreFilter === "All") {
                return this.discList;
            }

            return this.discList.filter((typeMusic) => {
                console.log(typeMusic)
                return this.genreFilter === typeMusic.genre;
            })
        }
    },

    methods: {
        onGenreFilter(genreToFilter) {
            this.genreFilter = genreToFilter;
        }
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