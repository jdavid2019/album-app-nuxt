<template lang="html">
  <div class="container">
    <h1 class="title">Álbums de la página</h1>
    <div class="columns is-multiline">
      <AlbumCard :album="album" v-for="album in albums" :key="album.id" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import env from '../config/env.js'
import AlbumCard from "~/components/AlbumCard";
export default {
name: "index",
  components: {
  AlbumCard
  },
  data() {
   return {
     albums: []
   }
  },
  mounted: async function() {
    // axios.get(`${env.endpoint}/albums`).then(response => {
    //  this.albums = response.data;
    //})
    let response = await axios.get(`${env.endpoint}/albums`);
    this.albums = response.data
  }
}
</script>

<style scoped>

</style>