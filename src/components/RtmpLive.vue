<template>
  <video
      id="my-player1"
      class="video-js
                vjs-default-skin
                vjs-big-play-centered"
      preload="auto"
      width="500"
      height="400"
      data-setup='{ "html5" : { "nativeTextTracks" : false } }'>
  </video>
</template>

<script>
import 'videojs-flash'
import {videojs} from "vue-video-player/dist/ssr";
export default {
  name: 'rtmp-live',
  props: {
    src: {
      type: String,
      default: 'rtmp://120.79.24.219/live/livestream'
    }
  },
  data () {
    return {
      options1: {
        autoplay: true, // 是否自动播放
        muted: false, // 是否静音
        controls: false,
        fluid: true, // 宽高自适应
        sources: [{
          src: 'rtmp://120.79.24.219/live/livestream',
          type: 'rtmp/flv'
        }]
      }
    }
  },
  mounted(){
    this.player1 = videojs('my-player1', this.options1, function onPlayerReady() {
      videojs.log('播放器已经准备好了!')
      this.on('play', function() {
        console.log('开始/恢复播放')
      })
      this.on('pause', function() {
        console.log('暂停播放')
      })
      this.on('ended', function() {
        console.log('结束播放')
      })
    })
    this.player1.play()
  }
}
</script>
