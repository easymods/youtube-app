<template>
  <div id="app">
      <SearchBar @onInputChange="onSubmit"/>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '@/components/SearchBar';
export default {
  name: 'App',
  components: {
    SearchBar,
  },
  methods: {
    onSubmit(term) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        methods: 'GET',
        params: {
          api_key: process.env.VUE_APP_API_KEY,
          type: 'video',
          part: 'snippets',
          q: term,
          
        }
      })
      .then(response => console.log(response))
    }
  }
}
</script>

<style>

</style>
