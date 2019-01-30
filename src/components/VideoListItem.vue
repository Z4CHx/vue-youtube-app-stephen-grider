<template>
    <li @click="onVideoSelect" class="media" key="video.etag">
        <img class="mr-3" :src="thumbnailURL">
        <div class="media-body">
                {{video.snippet.title}}
        </div>
    </li>
</template>



<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    methods: {
        onVideoSelect(){
            this.$emit('videoSelect',this.video)
        }
    },
    computed: {
        thumbnailURL() {
            return this.video.snippet.thumbnails.default.url;
        }
    }
}
</script>



<style scoped>
    li {
        display: flex;
        cursor: pointer;
    }

    li:hover {
        background-color: #eee;
    }
</style>
