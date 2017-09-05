<template lang="html">
  <div class="album flex-col">
    <div class="page-header flex-1 flex-row flex-center">
      <div class="header-item" :class="{selected: h.selected}" v-for="h in typeList">
        {{h.title}}
      </div>
    </div>
    <div class="advertise-block flex-row flex-center">
      <div class="show-box">
        <div class="card" v-for="ad in adList">
          {{ad.img}}
          <div class="tag">{{ad.typeTitle}}</div>
        </div>
      </div>
      <div class="index-row">
        <div class="point" :class="{selected: p === currentAd}" v-for="p in adList"></div>
      </div>
    </div>

    <div class="album-block flex-col" v-for="albumBlock in albumBlockList">
      <div class="title-row">
        <div class="title">
          {{albumBlock.title}}
        </div>
        <div class="sub-title">
          {{albumBlock.subTitle}}
        </div>
      </div>
      <div class="content-part">
        <div class="album-item flex-col" v-for="album in albumBlock.list">
          <div class="image-box">
            <div class="counts">{{album.counts}}</div>
            {{album.albumImage}}
          </div>
          <div class="album-title">{{album.title}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  // 标题的类型
  let typeList = [
    { title: '推荐', selected: true },
    { title: '排行榜', selected: false },
    { title: '歌单', selected: false },
    { title: '主播电台', selected: false },
    { title: '最新音乐', selected: false }
  ]
  // 广告
  let adList = [
    {
      img: '',
      typeTitle: '专栏',
      typeColor: 'red'
    },
    {
      img: '',
      typeTitle: '新歌首发',
      typeColor: 'red'
    },
    {
      img: '',
      typeTitle: 'MV首发',
      typeColor: 'red'
    },
    {
      img: '',
      typeTitle: '独家',
      typeColor: 'green'
    }
  ]
  // 热门精选
  let topList = [
    {
      albumImage: '',
      counts: '5200000',
      title: '2017年八月最新热歌TOP50'
    },
    {
      albumImage: '',
      counts: '520000',
      title: '2017年八月最新热歌TOP40'
    },
    {
      albumImage: '',
      counts: '23232',
      title: '2017年八月最新热歌TOP30'
    },
    {
      albumImage: '',
      counts: '5200000',
      title: '2017年八月最新热歌TOP20'
    },
    {
      albumImage: '',
      counts: '5200000',
      title: '2017年八月最新热歌TOP10'
    },
    {
      albumImage: '',
      counts: '5200000',
      title: '落日骑行',
      typeTitle: '电台节目'
    },
    {
      albumImage: '',
      counts: '5200000',
      title: '你还好吗？'
    },
    {
      albumImage: '',
      counts: '5200000',
      title: '2017年八月最新热歌TOP50'
    }
  ]

  export default {
    name: 'Album',
    data () {
      return {
        typeList,
        adList,
        currentAd: '',
        albumBlockList: [
          {
            title: '热门精选',
            subTitle: '',
            list: topList
          }
        ]
      }
    }
  }
</script>

<style lang="less" scoped>
  @import "../less/common.less";
  @color-line: #DDDDDD;

  .album {
    display: inline-block;
    overflow-y: auto;
    flex-grow: 1;
  }
  .page-header {
    width: 100%;
    border-bottom: 1px solid #EEE;
    font-size: 14px;

    .header-item {
      padding: 12px 0;
      width: 6em;
      text-align: center;

      &.selected {
        color: @theme-color;
      }
    }
  }
  // 广告
  .advertise-block {
    display: block;
    padding: 14px;
    height: 260px;
    width: 100%;

    .show-box {
      width: 100%;
      text-align: center;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: center;
      position: relative;

      .card {
        display: flex;
        position: relative;
        align-items: center;
        justify-content: center;
        border-radius: 5px;
        position: absolute;
        top: 0;

        height: 200px;
        width: 460px;
        background-color: #ddd;

        &:nth-of-type(1) {
          // background-color: red;
          background-image: url('../assets/album.png');
          background-repeat: no-repeat;
          background-size: cover;
          transform: translateX(-100px) scale(0.96) rotateY(60deg);
          transform-origin: 0 50%;
          z-index: 4;
        }
        &:nth-of-type(2) {
          background-color: green;
          transform: translateX(0px);
          z-index: 5;
        }
        &:nth-of-type(3) {
          transform: translateX(60px);
          z-index: 4;
        }
        // &:nth-of-type(4) {
        //   transform: translateX(-10px);
        // }
        .tag {
          position: absolute;
          bottom: 0.6em;
          right: -5px;
          background-color: @theme-color;
          color: white;
          font-size: 13px;
          line-height: 2em;
          padding: 0 0.7em;
          border-top-left-radius: 1em;
          border-bottom-left-radius: 1em;
        }
      }
    }
  }

  // 专辑
  .album-block {
    display: flex;
    padding: 0 20px;

    .title-row {
      border-bottom: 1px solid @color-line;
      margin-bottom: 20px;

      .title {
        font-size: 20px;
        display: inline-block;
        border-bottom: 4px solid @color-line;
      }
    }

    .content-part {
      display: flex;
      flex-direction: row;
      align-items: flex-start;
      flex-wrap: wrap;

      @album-size: 180px;
      .album-item {
        margin-right: 30px;
        margin-bottom: 30px;

        .image-box {
          position: relative;

          height: @album-size;
          width: @album-size;
          background-color: #ddd;

          .counts {
            position: absolute;
            top: 0;
            right: 0;
            background-color: rgba(0,0,0, 0.4);
            color: white;
          }
        }
        .album-title {
          text-align: left;
          width: @album-size;
          font-size: 14px;
          padding: 0.2em 0;
          line-height: 1.5em;
          letter-spacing: 2px;

          height: 3.4em;
        }
      }
    }
  }
</style>
