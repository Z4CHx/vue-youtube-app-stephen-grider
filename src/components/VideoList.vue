<template>
    <div>
        <ul class="list-unstyled">
        <VideoListItem @videoSelect="onVideoSelect" v-for="video in videos" :video="video" :key="video.etag" />
        </ul>
    </div>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
    name: 'VideoList',
    props: {
        videos: Array
    },
    methods: {
        onVideoSelect(video){
            this.$emit('videoSelect',video)
        }
    },
    components: {
        VideoListItem
    }
}

</script>

<style>
</style>
