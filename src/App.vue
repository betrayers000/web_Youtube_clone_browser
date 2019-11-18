<template>
  <div>
    Youtube
    <!-- <자식컴포넌트 @자식이올려준함수="부모가사용할함수"/>
          형태로 사용하면 된다. -->
    <SearchVar @inputChange="onInputChange"/>
    <VideoDetail :video="selectedVideo"/>
    <VideoList :videos="videos" @videoSelect="onVideoSelect"/>
  </div>
</template>

<script>
import SearchVar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'

import axios from 'axios'

const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
const API_URL = "https://www.googleapis.com/youtube/v3/search"
export default {
  name: 'app',
  components:{
    SearchVar,
    VideoList,
    VideoDetail,
  },
  data: function(){
    return {
      videos:[],  
      selectedVideo : null,
    }
  },
  methods:{
    onInputChange(inputValue){
      axios.get(API_URL, {
        params:{
          key: API_KEY,
          part: 'snippet',
          type: 'video',
          q: inputValue
        }
      }).then(res => {
        this.videos = res.data.items
      }).catch(err=>{
        console.log(err)
      })
    },
    onVideoSelect(video){
      this.selectedVideo = video
    },
  },
}
</script>

<style>

</style>