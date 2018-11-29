<template>
    <div id="app">
        <div id="masterBox">
            <div id="sortButtons">
                <!-- <button class="button" v-for="cat in categoryName"> {{ cat }} </button> -->
                <button class="button" @click="bensinOrder"> Bensín95 </button>
                <button class="button"> Dísel </button>
                <button class="button"> Bensín95 Afsláttur </button>
                <button class="button"> Dísel Afsláttur </button>
                <button class="button"> Fyrirtæki </button>
                
            </div>
            <div v-for="result in orderBensin95" class="box" id="resultContainer"> 
                <div>
                    <p style="border: solid 0px"> {{ result.bensin95 }} </p>
                </div>
                <div>
                    <p style="border: solid 0px"> {{ result.diesel }} </p>
                </div>
                <div>
                    <p style="border: solid 0px"> {{ result.bensin95_discount}} </p>
                </div>
                <div>
                    <p style="border: solid 0px"> {{ result.diesel_discount }} </p>
                </div>
                <div>
                    <p style="border: solid 0px"> {{ result.company }} </p>
                </div>
            </div>
        </div>
        <div id="copyright">
            <p>This website and its content is copyright of TheEliteCandyShop INC - © TheEliteCandyShop INC 2018. All rights reserved.</p>
        </div>
        <div id="hint">
            <p>Psst, hey you, yes you over there, just a little heads up, you can click the categories to sort ;^)</p>
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

    computed: {
        orderBensin95() {
            return this.results.filter(bensin => {
                return bensin.bensin95
            })
        }
    },

    methods: {
        bensinOrder() {
            this.orderBensin95    
        }
        
    }
}
</script>

<style lang="scss" src="./assets/app.scss">

</style>
