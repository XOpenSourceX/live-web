<template>
  <div class="home">
<!--    <div class="example-title"> # vue-video-player 播放 RTMP 流 </div>-->
<!--    <Row type="flex" justify="center" :gutter="20">-->
<!--      <Col :span="18">-->
<!--        <Row type="flex" justify="center" :gutter="20" >-->
<!--          <i-col :span="18" v-for="(item, i) in videoInfo" :key="`info-${i}`" style="margin-bottom:30px;">-->
<!--            <Card>-->
<!--              <p slot="title" style="">{{ item.title }}</p>-->
<!--              <div >-->
<!--                <RtmpLive :src="item.videoSrc"></RtmpLive>-->
<!--              </div>-->
<!--            </Card>-->
<!--          </i-col>-->
<!--        </Row>-->
<!--      </Col>-->
<!--    </Row>-->
<!--    <div class="example-title"> # vue-video-player 播放 HLS 流 </div>-->
<!--    <Row type="flex" justify="center">-->
<!--      <Col :span="18">-->
<!--        <HlsLive></HlsLive>-->
<!--      </Col>-->
<!--    </Row>-->
    <div class="example-title"> 测试直播 </div>
    <Row type="flex" justify="center">
      <Col :span="18">
        <Flv></Flv>
      </Col>
    </Row>
<!--    <div class="example-title"> # flv.js 播放 http-flv 视频流并截图</div>-->
<!--    <Button type="primary" size="large" style="margin:0 0 2em;" @click="captureImg">截图</Button>-->
<!--    <Row type="flex" justify="center" :gutter="40" style="margin-bottom:6em;">-->
<!--      <Col :span="9">-->
<!--        &lt;!&ndash; 网上没有可以用的 http-flv 视频流，所以这里用 flv 代替 &ndash;&gt;-->
<!--        <HttpFlv src="http://8.136.179.213:8080/live/livestream.flv"></HttpFlv>-->
<!--      </Col>-->
<!--      <Col :span="9">-->
<!--        <div style="width:0px;height:0px;overflow:hidden;">-->
<!--          <canvas id="canvas" width="515" height="300"></canvas>-->
<!--        </div>-->
<!--        <img :src="imgSrc" style="margin-top:5px;"/>-->
<!--      </Col>-->
<!--    </Row>-->
  </div>
</template>

<script>
import GithubButton from 'vue-github-button'
import RtmpLive from "@/components/RtmpLive.vue";
import HlsLive from "@/components/HlsLive.vue";
import Flv from "@/components/flv.vue";
import HttpFlv from "@/components/httpFlv.vue";

export default {
  name: "home",
  components: {
    // GithubButton,
    // RtmpLive,
    // HlsLive,
    Flv,
    // HttpFlv
  },
  data () {
    return {
      title: 'web 播放视频流/直播',
      subtitle: '使用 vue-video-player、flv.js 播放 RTMP、HLS、HTTP-FLV 视频流',
      videoInfo: [
        { title: '测试', videoSrc: 'rtmp://8.136.179.213/live/livestream'},
      ],
      imgSrc: '', // 图片路径
      canvas: '',
      context: '',
      videoTag: ''
    }
  },
  mounted () {
    this.videoTag = document.getElementById('videoElement2')
    this.canvas = document.getElementById('canvas')
    this.context = this.canvas.getContext('2d')
    console.log('加载数据：', this.videoTag, this.canvas, this.context)
  },
  methods: {
    captureImg () {
      this.context.drawImage(this.videoTag, 0, 0, 515, 300)
      let base64 = this.canvas.toDataURL('image/jpeg')
      console.log('base64:', base64)
      this.imgSrc = base64
    }
  }
};
</script>

<style lang="less" scoped>
a {
  // color: #42b983;
  color: #fff;
}
a:hover {
  color: #fff;
}
.title {
  height: 1em;
  line-height: 1em;
  font-weight: 700;
  font-size: 4rem;
  margin: 1.5em 0 1.2em;
}
.subtitle {
  font-size: 1.8em;
  color: #a5a5a5;
  margin: 1em 0;
  font-weight: bold;
}
.actions {
  margin-top: 3em;
  margin-bottom: 2em;
}
.example-title {
  font-size: 1.8em;
  font-weight: bold;
  margin-top: 3em;
  margin-bottom: 2em;
}
</style>

