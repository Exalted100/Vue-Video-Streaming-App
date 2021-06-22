<template>
  <div class="search-container">
    <input type="text" name="search" placeholder="Search" id="" aria-label="search bar" v-model="searchValue">
    <button v-on:click="makeVideoRequest" aria-label="search submit button"><div class="image-container"><img src="../assets/search-line.svg" alt="search icon"></div></button>
  </div>
  <div v-show="videoPlaying">
      <iframe width="1120" height="630" src="https://www.youtube.com/embed/D1e7EXHh8tg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </div>
  <div class="video-list-container">
      <VideoData v-for="video in videos" v-bind:video="video" v-bind:key="video.id.videoId" ></VideoData>
  </div>
</template>

<script>
import axios from "axios"
import VideoData from './VideoData.vue'
import apiKey from "../keys.js"

export default {
  name: 'Search',
  components: {
      VideoData
  },
  data() {
    return {
        apiKey: "AIzaSyDV4CrnBqdxolhzpp0aMMRSnA-CXfMiHZo",
        searchValue: "",
        videos: [],
        videoPlaying: false
    }
  },
  methods: {
      async makeVideoRequest() {
            const result = await axios.get(`https://www.googleapis.com/youtube/v3/search?part=snippet&q=${this.searchValue}&key=${apiKey}&maxResults=20&type=video&videoEmbeddable=true&videoDefinition=high`)
            this.videos = result.data.items
            console.log(this.videos)
          }
      }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search-container {
    text-align: center;
    padding-top: 1rem;
    padding-bottom: 1rem;
    display: flex;
    flex-wrap: nowrap;
    background-color: rgb(243, 243, 243);
    justify-content: center;
}

.image-container {
    width: 1rem;
    height: 1rem;
    margin: 0 auto;
}

.image-container > img {
    max-width: 100%;
}

input {
    height: 2rem;
    width: 30rem;
    letter-spacing: 0.1rem;
    padding: 0.5rem;
}

input::placeholder {
    color: grey;
}

button {
    height: 2rem;
    width: 3rem;
}

.video-list-container {
    width: 70%;
    margin: 0 auto;
}
</style>
