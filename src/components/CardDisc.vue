<template>
    <div class="card">
        <img class="card-img-top" :src="poster" alt="...">
        <div class="card-body">
            <h1 class="card-title text-center ">{{ title.toUpperCase() }}</h1>
            <div class="card-text text-center">
                <h5>{{author}}</h5>
                <h5>{{year}}</h5>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:"CardDisc",
    props: {
        author: String,
        genre: String,
        poster: String,
        title: String,
        year: String,
    }
}
</script>