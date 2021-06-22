<template>
  <div class="video-container">
    <div><img v-bind:src="video.snippet.thumbnails.default.url" alt="video thumbnail"></div>
    <div>
        <h3>{{ video.snippet.title }}</h3>
        <h6>{{ video.snippet.channelTitle }}</h6>
        <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Search',
  props: [ "video" ],
  data() {
      return {
          thumbnail: "https://i.ytimg.com/vi/xtGsaxqpx_U/mqdefault.jpg"
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 .video-container {
     display: flex;
     flex-wrap: nowrap;
 }
</style>
