<template>
    <div class="container">
       <searchbar @termChange = "onTermChange"></searchbar>
       <div class = "row">
       <videodetail :video = "selectedVideo"></videodetail>
       <videolist @videoSelect = "onVideoSelect" :videos = "videos"></videolist>
       </div>
       <!-- {{ videos.length }} -->
    </div>
</template>

<script>
import axios from 'axios';
import searchbar from './components/SearchBar';
import videolist from './components/VideoList';
import videodetail from './components/VideoDetail';
const API_KEY = 'AIzaSyDIO2okT9FJtyYDbnWbkrq53B_WAZiespI';

export default{
    name : 'App',
    components :{ 
        searchbar,
        videolist,
        videodetail
    },
    data(){
        return{
            videos : [],
            selectedVideo : null
        };
    },
    methods : {
        onVideoSelect(video){
            this.selectedVideo = video;
        },
        onTermChange(term){
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params : {
                    key : API_KEY,
                    type : 'video',
                    part: 'snippet',
                    q: term
                }
            }).then(response => {
                this.videos = response.data.items;
                console.log(this.videos)
               
            });
        }
    }
};
</script>