<template>
    <div v-if = "video" class="col-md-8">
        <div class="ratio ratio-16x9">
            <iframe class="embed-responsive-item" :src="videoUrl"></iframe>
        </div>
        <div class="details">
            <h4>{{ video.snippet.title }}</h4>
            <p>{{ video.snippet.description}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name : 'videodetail',
    props : ['video'],
    computed : {
        videoUrl(){
            const videoId = this.video.id.videoId;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>

<style scoped>
    .details{
        border: 1px solid #ddd;
        padding: 10px;
        border-radius: 4px;
        margin-top:10px;
    }
</style>