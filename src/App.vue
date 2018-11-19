<template>
    <div id="app">
        <div id="masterBox">
            <div id="headers">
                <h1 style="border: solid 1px"> Bensín95 </h1>
                <h1 style="border: solid 1px"> Bensín95 Afsláttur </h1>
                <h1 style="border: solid 1px"> Diesel </h1>
                <h1 style="border: solid 1px"> Diesel Afsláttur </h1>
                <h1 style="border: solid 1px"> Company </h1>
            </div>
            <div v-for="result in results" class="box" id="resultContainer">
                <p> {{ result.bensin95 }} </p>
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
            results: []
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
