<template>
  <li @click="onVideoSelect" class="list-group-item">
    <img :src="thumbnailURL" alt="">
    {{video.snippet.title}}
  </li>
</template>

<script>
export default {
  name: 'videoListItem',
  props:{
    video:Object
  },
  computed:{
    thumbnailURL : function(){
      return this.video.snippet.thumbnails.default.url
    }
  },
  methods:{
    onVideoSelect(){
      this.$emit('videoSelect', this.video)
    }
  }
}
</script>

<style>

</style>