<template>
    <div class="column">
        <div class="b-card" style="width: 18rem;">
            <div class="image-container" @click="toggleDescription">
                <img :src="beer.image_url" class="card-img-top" alt="beer">
            </div>
            <div class="card-body">
                <h5 class="card-title">{{ beer.name }} {{ beer.abv }}°</h5>
                <p class="card-text">{{ beer.tagline }}</p>
                <p class="description" v-if="showDescription">{{ beer.description }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            beer: Object,
        },
        data() {
            return {
                showDescription: false
            }
        },
        methods: {
            toggleDescription() {
                this.showDescription = !this.showDescription;
            }
        }
    }
</script>

<style>
    .image-container {
        height: 150px;
        display: flex;
        margin: 10px;
        justify-content: center;
        background-color: #41B882;
        border-radius: 5px;
        border-style: solid;
        border-color: white;
        border-width: 1px;
    }

    .image-container img {
        width: auto;
        height: 100%;
        margin: auto;
    }

    .image-container:hover {
        opacity: 50%
    }

    p {
        color: white;
        text-align: center;
    }

    h5 {
        text-align: center;
        font-size: 100px;
        color: white;
    }
</style>
