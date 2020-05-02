<template>
  <div id="app">
      <SearchBar @onInputChange="onSubmit"/>
      <VideoList :videos="videos"/>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '@/components/SearchBar';
import VideoList from '@/components/VideoList';
export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
  },
  data() {
    return {
      videos: [],
    }
  },
  methods: {
    onSubmit(term) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        methods: 'GET',
        params: {
          key: process.env.VUE_APP_API_KEY,
          type: 'video',
          part: 'snippet',
          q: term,
          
        }
      })
      .then(response => {
        this.videos = response.data.items;
      })
    }
  }
}
</script>

<style>

</style>
