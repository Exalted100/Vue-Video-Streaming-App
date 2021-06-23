<template>
  <div class="video-container">
    <div class="thumbnail-container"><img v-bind:src="video.snippet.thumbnails.high.url" alt="video thumbnail"></div>
    <div class="video-details-container">
        <h3>{{ video.snippet.title }}</h3>
        <h6>by {{ video.snippet.channelTitle }}</h6>
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
     margin: 1rem 0;
     cursor: pointer;
 }

 .video-container:hover {
     background-color: rgb(245, 245, 245);
 }

.thumbnail-container {
    flex: 0.3;
}

.thumbnail-container > img {
    max-width: 100%;
}

.video-details-container {
    flex: 0.7;
    padding: 2rem;
}

h3 {
    font-size: 2rem;
    margin-bottom: 1rem;
}

h6 {
    font-size: 1rem;
    font-weight: 500;
    margin-bottom: 0.5rem;
}
</style>
