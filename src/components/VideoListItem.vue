<template>
    <div class="item">
        <div class="image">
            <img :src="imageUrl">
        </div>
        <div class="content">
            <a class="header" @click="onVideoSelect">{{video.snippet.title}}</a>
        <div class="meta">
            <span>{{video.snippet.description}}</span>
        </div>
        <div class="description">
            <p></p>
        </div>
        <div class="extra">
            Published: {{dateToString}}
        </div>
    </div>
    </div>
</template>

<script>
    export default {
        props: ['video'],
        computed: {
            imageUrl() {
                return this.video.snippet.thumbnails.default.url;
            },
            dateToString() {
                const videoPublished = new Date(this.video.snippet.publishedAt);
                return videoPublished.toLocaleString();
            }
        },
        methods: {
            onVideoSelect() {
                this.$emit('onVideoSelected', this.video);
            }
        }
    }
</script>

<style>

</style>