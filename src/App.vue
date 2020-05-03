<template>
  <div id="app">
      <SearchBar @onInputChange="onSubmit"/>
      <VideoDetail :selectedVideo='selectedVideo'/>
      <VideoList :videos="videos" @onVideoSelected='onVideoSelect'/>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '@/components/SearchBar';
import VideoList from '@/components/VideoList';
import VideoDetail from '@/components/VideoDetail';
export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: [],
      selectedVideo: null,
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
    },
    onVideoSelect(video){
      this.selectedVideo = video;
    }
  }
}
</script>

<style>

</style>
