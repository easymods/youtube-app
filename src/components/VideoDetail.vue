<template>
    <div v-if="selectedVideo">
        {{selectedVideo.snippet.title}}
    </div>
</template>

<script>
    export default {
        props: ['selectedVideo']
    }
</script>

<style>

</style>