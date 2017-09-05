<template lang="html">
  <div class="play-box flex-row">
    <div class="album-cover-image" :style="imgBg(Icons.scene)"></div>
    <div class="flex-row flex-1">
      <div class="msg">
        <div class="title">约定(Live)</div>
        <div class="artist">陈奕迅</div>
      </div>
      <div class="actions">
        <div class="icon" :style="imgBg(Icons.iconShare)"></div>
        <div class="icon" :style="imgBg(Icons.iconHeartLine)"></div>
      </div>
    </div>
  </div>
</template>

<script>
  import Icons from '../assets/Image/index.js'

  export default {
    name: 'PlayBox',
    data () {
      return {
        Icons
      }
    },
    methods: {
      imgBg (url) {
        return {
          backgroundImage: `url(${url})`
        }
      }
    }
  }
</script>

<style lang="less" scoped>
  @import "../less/common.less";

  .play-box {
    background-color: #F5F4F5;
    border-top: 1px solid #ccc;
    padding: 10px;
    display: flex;
    flex-shrink: 0;
    height: 80px;
    width: 100%;
    display: flex;
    flex-direction: row;
    padding-right: 5px;

    .album-cover-image {
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center;
      border-radius: 2px;
      height: 60px;
      width: 60px;
      flex-shrink: 0;
    }
    .msg {
      flex: 1;
      padding: 5px;

      .artist,
      .title {
        width: 100%;
        white-space: nowrap;
        text-overflow: ellipsis;
      }
      .title {

      }
      .artist {
        color: #666;
        font-size: 12px;
        margin-top: 5px;
      }

    }
    .actions {
      flex-shrink: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-around;
      height: 100%;
      padding: 6px 0;

      .icon {
        display: inline-block;
        height: 15px;
        width: 15px;
        background-position: center;
        background-repeat: no-repeat;
        background-size: contain;
      }
    }
  }
</style>
