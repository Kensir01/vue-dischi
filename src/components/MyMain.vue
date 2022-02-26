<template>
    <main>
        
            <div class="container">

                <div class="row row-cols-5 justify-center py-5">

                    <CardMusic 
                    v-for="(details, indice) in dischi" 
                    :key="indice" 
                    :details="details"
                    />

                </div>

            </div>
       
    </main>
</template>

<script>
const axios = require('axios');
import CardMusic from './partials/CardMusic.vue';
export default {
    name: 'MyMain',
    data() {
        return {
            dischi: [],
            loadingInPorgress: true, 
        }
    },
    components: {
        CardMusic
    },
    methods: {
        getMusic() {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                this.dischi = response.data.response;
                this.loadingInPorgress = false;
            })
            .catch(function(error) {
                console.log(error);
            })
        }
    },
    created() {
        this.getMusic();
    }
}
</script>

<style scoped lang="scss">
main {
    background-color: #1e2d3b;
    min-height: calc(100vh - 80px);
}
</style>