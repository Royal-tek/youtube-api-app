<template>
    <div class="col-md-4">
    <ul class="list-group">
        <VideoListItem v-for="video in videos " :key="video.etag" :video = "video" @videoSelect = "onVideoSelect"></VideoListItem>
    </ul>
    </div>
</template>

<script>
import VideoListItem from './VideoListItem.vue'

export default {
    name : 'videolist',
    components : {
        VideoListItem,
    },
    props : ['videos'],
    methods : {
        onVideoSelect(video){
            this.$emit('videoSelect', video)
        }
    }
}
</script>

<style>
    
</style>