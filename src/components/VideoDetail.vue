<template>
    <div v-if="selectedVideo" class="ui segment">
        <iframe class="ui video" :src="videoUrl"></iframe>

        <div class="item">
            <div class="content">
                <a class="header">{{selectedVideo.snippet.title}}</a>
                <div class="description">
                    <p>{{selectedVideo.snippet.description}}</p>
                </div>
                <div class="extra">
                    Published: {{dateToString}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['selectedVideo'],
        computed: {
            videoUrl() {
                const videoID = this.selectedVideo.id.videoId;
                return `https://www.youtube.com/embed/${videoID}`
            },

            dateToString() {
                const videoPublished = new Date(this.selectedVideo.snippet.publishedAt);
                return videoPublished.toLocaleString();
            }
        },
    }
</script>

<style>
.ui .video {
    width: 100%;
    min-height: 500px;
}
</style>