<template>
  <video id="videoElement2" style="background-color:#fff;height:300px;width:100%;"></video>
</template>

<script>
import flvjs from 'flv.js'

export default {
  name: 'httpflv',
  props: {
    src: {
      type: String,
      default: 'http://120.79.24.219:8080/live/livestream.flv'
      // default: 'http://192.168.9.12:8080/live?app=live&stream=stream'
    }
  },
  data () {
    return {
    }
  },
  mounted () {
    let flvSrc = this.src
    console.log('flvSrc:', flvSrc)
    if (flvjs.isSupported()) {
      var videoElement = document.getElementById('videoElement2')
      var flvPlayer = flvjs.createPlayer({
        type: 'flv',
        // url: 'http://yunxianchang.live.ujne7.com/vod-system-bj/TLaf2cc9d469939803949187b46da16c45.flv'
        url: flvSrc
      })
      flvPlayer.attachMediaElement(videoElement)
      flvPlayer.load()
      flvPlayer.play()
    }
  }
}
</script>

<style lang="less" scoped>

</style>
