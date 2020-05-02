<template>
    <div class="main">
        <div class="ui container">
            <div class="main-videos">
                <VideoListItem v-for="video in videos" 
                :key="video.etag"
                :video="video"
                />
            </div>
        </div>
    </div>
</template>

<script>
import VideoListItem from '@/components/VideoListItem'
    export default {
        props: ['videos'],
        components: {
            VideoListItem,
        }
    }
</script>

<style>

</style>