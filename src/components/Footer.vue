<template lang="html">
  <div class="footer flex-center flex-row">
    <div class="control-box flex-row flex-bi-center">
      <div class="btn-pre"><span class="icon" :style="imgBg(Icons.iconSongPre)"></span></div>
      <div class="btn-play"><span class="icon" :style="imgBg(Icons.iconSongPlay)"></span></div>
      <div class="btn-next"><span class="icon" :style="imgBg(Icons.iconSongNext)"></span></div>
    </div>
    <div class="process-box flex-row">
      <div class="bar">
        <div class="bar-bg"></div>
        <div class="bar-fill" :style="{width: songProcessRatio}"></div>
        <div class="bar-point" :style="{left: songProcessRatio}"></div>
      </div>
    </div>
    <div class="time-box flex-row">
      <div class="current-time">{{this.currentTime | timeTag}}</div>
      /
      <div class="duration-time">{{this.totalDuration | timeTag}}</div>
    </div>

    <div class="volumn-box flex-row">
      <div class="icon-volumn icon"><span class="icon" :style="imgBg(Icons.iconVolumn)"></span></div>
      <div class="bar">
        <div class="bar-bg"></div>
        <div class="bar-fill" :style="{width: toRatio(volumnRatio)}"></div>
        <div class="bar-point" :style="{left: toRatio(volumnRatio)}"></div>
      </div>
    </div>

    <div class="utils-box flex-row">
      <div class="btn-play-mode"><span class="icon" :style="imgBg(Icons.iconPlaymodeCircle)"></span></div>
      <div class="btn-lyrics"><span class="icon" :style="imgBg(Icons.iconLyric)"></span></div>
      <div class="btn-playlist-box">
        <div class="icon-playlist"><span class="icon" :style="imgBg(Icons.iconPlaylist)"></span></div>
        <div class="counts">23</div>
      </div>
    </div>
  </div>
</template>

<script>
  import Icons from '../assets/Image/index.js'

  const MINUTE = 60
  function TimeTag (minute, second) {
    return minute * MINUTE + second
  }
  function fillZero (v, digits = 2) {
    return `00${v}`.substr(-digits)
  }

  export default {
    name: 'Footer',
    data () {
      return {
        Icons,
        volumnRatio: 0.3,
        totalDuration: TimeTag(8, 48),
        currentTime: TimeTag(4, 39)
      }
    },
    computed: {
      songProcessRatio () {
        return this.toRatio(this.currentTime / this.totalDuration)
      }
    },
    filters: {
      timeTag (v) {
        let m = Math.floor(v / MINUTE)
        let s = v - MINUTE * m
        return `${fillZero(m)}:${fillZero(s)}`
      }
    },
    methods: {
      imgBg (url) {
        return {
          backgroundImage: `url(${url})`
        }
      },
      toRatio (v) {
        return `${v * 100}%`
      }
    }
  }
</script>

<style lang="less" scoped>
  @import "../less/common.less";
  .icon {
    display: inline-block;
    height: 22px;
    width:  22px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
  }
  // 进度条公用
  .bar {
    position: relative;
    @bar-height: 5px;

    .bar-bg {
      height: @bar-height;
      border-radius: @bar-height/2;
      width: 100%;
      background-color: #ddd;
    }
    .bar-fill {
      position: absolute;
      left: 0;
      top: 0;
      height: @bar-height;
      border-radius: @bar-height/2;
      width: 20%;
      background-color: #D03232;
    }
    .bar-point {
      @point-size: 12px;

      position: absolute;
      background-color: white;
      border: 1px solid rgba(99,99,99,0.3);
      height: @point-size;
      width:  @point-size;
      margin-left: -@point-size/2;
      border-radius: 50%;
      top: (@bar-height - @point-size)/2;
      left: 20%;
    }
  }

  .footer {
    height: 60px;
    background-color: #F6F6F6;
    border-top: #C5C5C5 1px solid;
    flex-shrink: 0;
  }
  .control-box {
    width: 180px;
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 0 10px;
    .icon {
      display: inline-block;
    }
    .btn-pre,
    .btn-next {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 36px;
      width:  36px;
      border-radius: 50%;
      background-color: #D03232;

      .icon {
        display: inline-block;
        height: 16px;
        width:  16px;
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
      }
    }
    .btn-play {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 40px;
      width:  40px;
      border-radius: 50%;
      background-color: #D03232;

      .icon {
        display: inline-block;
        height: 22px;
        width:  22px;
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
      }
    }
  }
  .process-box {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    .bar {
      display: inline-block;
      height: 5px;
      width: 100%;
    }
  }
  .time-box {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-left: 8px;
    margin-right: 12px;
    font-size: 12px;
    align-items: center;

    div {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
    }
  }
  .volumn-box {
    display: flex;
    align-items: center;
    justify-content: center;
    .icon-volumn {
      margin-right: 4px;
    }
    .bar {
      width: 90px;
      margin-left: 4px;
    }
  }

  .utils-box {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content:space-around;
    padding: 0 10px;
    width: 150px;

    .btn-playlist-box {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;

      .counts {
        display: inline-block;
        margin-left: 2px;
        background-color: #ccc;
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 0 5px;
        font-size: 12px;
        border-radius: 0.5em;
      }
    }
  }
</style>
