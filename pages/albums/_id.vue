<template>
<h1>{{album.title}}</h1>
</template>

<script>
//gracias a esta libreria podemos tener aacceso a un objeto route
import router from 'vue-router'
import axios from 'axios';
import env from '../../config/env.js';
export default {
  name: "AlbumsIndividualPages",
  data() {
    return {
      album: {},
      photos: []
    }
  },
  mounted() {
    axios.get(`${env.endpoint}/albums/${this.$route.params.id}`)
    .then(albumResponse=>{
      this.album = albumResponse.data
    })
    //console.log(this.$route)
    //let albumId = this.$route.params.id;
    //console.log(albumId)
  }
}
</script>

<style scoped>

</style>