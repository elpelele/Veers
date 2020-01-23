<template>
    <div class="app" id="app">
        <div class=massive-container>
            <div class="logo">
                <img src="./assets/logo.png" alt="logo">
                <h1 class="eers">EERS</h1>
            </div>
            <input class="searchBar" type="search" v-model="field" placeholder="Find a beer">
            <div class="row beer-container">
                <div v-for="beer in filteredBeers" :key="beer.id">
                    <Beer :beer='beer'/>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
    import Axios from "axios";
    import Beer from "./components/Beer";

    export default {
        components: {
            Beer
        },
        data: function () {
            return {
                beers: [],
                field: '',
            }
        },
        mounted() {
            Axios
                .get('https://api.punkapi.com/v2/beers')
                .then(response => (this.beers = response.data))
        },
        computed: {
            filteredBeers() {
                return this.beers.filter((beer) => {
                    return beer.name.includes(this.field)
                })
            }
        }
    }

</script>


<style scoped>

    .app {
        background-color: #35495E;
        background-size: cover;
    }

    .logo {
        justify-content: center;
        background-color: white;
        display: flex;
        border-radius: 15px;
        padding-top: 15px;
    }

    .massive-container {
        margin: auto;
        width: 50%;
    }

    .eers {
        text-align: center;
        font-size: 100px;
        color: #41B882;
    }

    .searchBar {
        height: 50px;
        width: 100%;
        margin: 50px 0;
    }

    .beer-container {
        justify-content: center;
    }

    @media screen and (max-width: 991px) {
        .eers {
            font-size: 0
        }
    }
</style>
