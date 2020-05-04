<template>
    <div class="ui divided items">
        <VideoListItem v-for="video in videos" 
        :key="video.etag"
        :video="video"
        @onVideoSelected="onVideoSelect"
        />
    </div>
</template>

<script>
import VideoListItem from '@/components/VideoListItem'
    export default {
        props: ['videos'],
        components: {
            VideoListItem,
        },
        methods: {
            onVideoSelect(video) {
                this.$emit('onVideoSelected', video);
            }
        }
    }
</script>

<style>

</style>