<template>
  <div>
    <video id="videoElement" controls autoplay  style="height:600px;width:100%;">
    </video>
<!--    <button @click="play">播放</button>-->
  </div>
</template>

<script>
import flvjs from 'flv.js'
export default {
  data () {
    return {
      flvPlayer:null
    }
  },
  mounted() {
    if (flvjs.isSupported()) {
      var videoElement = document.getElementById('videoElement');
      this.flvPlayer = flvjs.createPlayer({
        type: 'flv',
        isLive: true,
        hasAudio: true,
        url: 'http://120.79.24.219:8080/live/livestream.flv'		// 自己的flv视频流
      });
      this.flvPlayer.attachMediaElement(videoElement);
      this.flvPlayer.load();
      this.flvPlayer.play();
    }
  },

  created() {
    this.flvPlayer.play();
  },

  methods:{
    play () {
      this.flvPlayer.play();
    }
  }
}
</script>

<style lang="less" scoped>

</style>
