<template>
  <Search />
  <h2>Only available on Desktop</h2>
</template>

<script>
import Search from './components/Search.vue'

export default {
  name: 'App',
  components: {
    Search
  }
}
</script>

<style>
*, *::before, *::after {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  max-width: 100%;
}

h2 {
  display: none;
}

@media only screen and (max-width: 900px) {
  h2 {
    display: block;
    text-align: center;
    padding-top: 5rem;
  }
}
</style>
