<template>
  <div id="app">
    <div class="container">
      
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {

    name: 'app',
 
    mounted() {
        axios.get("http://apis.is/petrol")
            .then(response => {
                this.results = response.data.results})
    },

}
</script>

<style lang="scss" src="./assets/app.scss">

</style>
