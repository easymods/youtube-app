<template>
  <div id="app">
    <div class="ui container">
      <SearchBar @onInputChange="onSubmit"/>
      <div class="ui grid">
        <div class="ten wide column">
          <VideoDetail :selectedVideo='selectedVideo'/>
        </div>
        <div class="six wide column" :class="[selectedVideo ? 'six wide column' : 'sixteen wide column' ]">
          <VideoList :videos="videos" @onVideoSelected='onVideoSelect'/>
        </div>
      </div>
    </div>
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
