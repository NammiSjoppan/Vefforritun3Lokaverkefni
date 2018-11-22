<template>
    <div id="app">
        <div id="masterBox">
            <div id="sortButtons">
                <button class="button" style="border: solid 1px" v-for="cat in categoryName"> {{ cat }} </button>
                
            </div>
            <div v-for="result in results" class="box" id="resultContainer">   
                <p style="border: solid 0px"> {{ result.bensin95 }} </p>
                <p style="border: solid 0px"> {{ result.bensin95_discount }} </p>
                <p style="border: solid 0px"> {{ result.diesel }} </p>
                <p style="border: solid 0px"> {{ result.diesel_discount }} </p>
                <p style="border: solid 0px"> {{ result.company }} </p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {

    name: 'app',

    data() {
        return{
            results: [],
            categoryName: ['Bensín95', 'Dísel', 'Bensín95 Afsláttur', 'Dísel Afsláttur', 'Fyrirtæki']
        }
    },
 
    mounted() {
        axios.get("http://apis.is/petrol")
            .then(response => {
                this.results = response.data.results})
    },

}
</script>

<style lang="scss" src="./assets/app.scss">

</style>
