<template>
  <div class="container">
    <header>
      <nuxt-link to="/">Regresar</nuxt-link>
      <h1 class="title">{{album.title}}</h1>
    </header>
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
        <img :src="photo.url" :alt="photo.title">
      </div>
    </div>
  </div>
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
  mounted: async function() {
    //  axios.get(`${env.endpoint}/albums/${this.$route.params.id}`)
    //   .then(albumResponse=>{
    //  this.album = albumResponse.data
    // });
    // axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
    //    .then(photosResponse=>{
    //      this.photos = photosResponse.data
    // Replace to
     let albumResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}`);
     this.album = albumResponse.data;
     let photoResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`);
     this.photos = photoResponse.data;
    }
    //console.log(this.$route)
    //let albumId = this.$route.params.id;
    //console.log(albumId)
}
</script>

<style scoped>
.container {
  text-align: center;
}

</style>