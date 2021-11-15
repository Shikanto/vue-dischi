<template>
    <div class="row row-cols-1 row-cols-md-5 g-4">
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

export default {
    name:"DiscContainer",
    components: {CardDisc},
    data() {
        return {
            discList: [],
        };
    },
    mounted() {
        axios.get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((resp) =>{
        this.discList.push(...resp.data.response)
        });
    }
}
</script>
<style lang="scss" scoped>

</style>