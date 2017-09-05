<template lang="html">
  <div class="panel">
    <div class="list-block" v-for="lb in list">
      <div class="list-header flex-row">
        <span>
          {{lb.title}}
        </span>
        <span class="action">
          {{lb.icon}}
        </span>
      </div>

      <div class="list-content">
        <div class="list-item flex-row flex-middle"
          :class="{selected: listItem.selected}"
          @click="selectRow(listItem)"
          v-for="listItem in lb.list">
          <div class="icon" :style="imgBg(listItem.icon)"></div>
          <div class="list-item-title">{{listItem.title}}</div>
          <div class="red-point" v-if="listItem.showHint"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Icons from '../assets/Image/index.js'

  let contentList = [
    {
      title: '推荐',
      action: {
        icon: '',
        title: ''
      },
      list: [
        {
          icon: Icons.iconPlaylist,
          title: '发现音乐',
          selected: true,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '私人FM',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: 'MV',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '朋友',
          selected: false,
          showHint: true
        }
      ]
    },
    {
      title: '我的音乐',
      action: {
        icon: Icons.iconPlaylist,
        title: ''
      },
      list: [
        {
          icon: Icons.iconPlaylist,
          title: 'iTunes音乐',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '下载的音乐',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '我的歌手',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '我的MV',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '我的电台',
          selected: false,
          showHint: false
        }
      ]
    },
    {
      title: '创建的歌单',
      action: {
        icon: Icons.iconPlaylist,
        title: ''
      },
      list: [
        {
          icon: Icons.iconPlaylist,
          title: '我喜欢的音乐',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '陈奕迅',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: 'The Piano Player',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '我喜欢的音乐',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '陈奕迅',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: 'The Piano Player',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '我喜欢的音乐',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '陈奕迅',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: 'The Piano Player',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '我喜欢的音乐',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '陈奕迅',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: 'The Piano Player',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '我喜欢的音乐',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '陈奕迅',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: 'The Piano Player',
          selected: false,
          showHint: false
        },
        {
          icon: Icons.iconPlaylist,
          title: '朋友',
          selected: false,
          showHint: false
        }
      ]
    }
  ]

  export default {
    name: 'Panel',
    data () {
      return {
        list: contentList,
        Icons
      }
    },
    methods: {
      imgBg (url) {
        return {
          backgroundImage: `url(${url})`
        }
      },
      selectRow (row) {
        let allItem = this.list
        allItem.map(item => {
          let list = item.list
          list.forEach(i => {
            i.selected = false
          })
        })

        row.selected = true
      }
    }
  }
</script>

<style lang="less" scoped>
  @import "../less/common.less";

  @font-color: #393939;

  .panel {
    position: relative;

    .list-block {
      margin-bottom: 10px;

      .list-header {
        padding: 3px 6px;
        font-size: 12px;
        color: #bbb;
      }
      .list-content {
        cursor: pointer;

        .list-item {
          color: @font-color;
          font-size: 13px;
          padding: 6px 6px;

          .icon {
            display: inline-block;
            width: 1em;
            height: 1em;
            overflow: hidden;
            margin: 0 8px;
          }
          &.selected {
            background-color: #E1E1E1;
            position: relative;

            &:before {
              display: inline-block;
              content: ' ';
              height: 70%;
              width: 2px;
              position: absolute;
              top: 15%;
              left: 0;
              background-color: @theme-color;
            }
            background-color: #eee;
          }

          .red-point {
            position: relative;
            top: -3px;
            left: 3px;
            @red-point-size: 8px;
            display: inline-block;
            height: @red-point-size;
            width: @red-point-size;
            border-radius: 50%;
            background-color: @theme-color;
          }
        }
      }
    }

  }
</style>
