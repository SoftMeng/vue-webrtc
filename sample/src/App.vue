<template>
  <div id="app" class="container">
    <h5>WebRTC Room</h5>
    <br>
    <div class="row">
      <input v-model="roomId" placeholder="请输入房间号">
    </div>
    <div class="row">
      <button class="button button-outline float-left" style="margin-right:8px;" @click="onJoin">加入</button>
      <button class="button button-outline float-left" style="margin-right:8px;" @click="onShareScreen">分享屏幕</button>
      <button class="button float-left" @click="onLeave">关闭</button>
    </div>
    <br/>
    <div class="row" style="width: 2000px">
      <vue-webrtc
        :roomId="roomId"
        ref="webrtc"
        width="100%"
        cameraHeight="400px"
        autoplay=true
        enableAudio=true
        enableVideo=true
        enableLogs=false
        screenshotFormat="image/jpeg"/>
    </div>
  </div>
</template>

<script>
  import Vue from 'vue'
  import { WebRTC } from 'vue-webrtc';

  Vue.component(WebRTC.name, WebRTC);

  export default {
    name: 'app',
    components: {
    },
    data() {
      return {
        img: null,
        roomId: ""
      };
    },
    computed: {
    },
    watch: {
    },
    methods: {
      onJoin() {
        this.$refs.webrtc.join();
      },
      onLeave() {
        this.$refs.webrtc.leave();
      },
      onShareScreen() {
        this.img = this.$refs.webrtc.shareScreen();
      },
    }
  };









</script>
