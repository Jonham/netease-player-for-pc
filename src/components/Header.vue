<template lang="html">
  <div class="header flex-col">
    <div class="window-btns flex-row flex-between">
      <div class="left flex-row">
        <div class="flex-bi-center btn-close">x</div>
        <div class="flex-bi-center btn-min">-</div>
        <div class="flex-bi-center btn-max">+</div>
      </div>
      <div class="right flex-row">
        <div class="btn-panel">-</div>
      </div>
    </div>

    <div class="content flex-row flex-between">
      <div class="left flex-row flex-bi-center">
        <div class="logo">
          <img :src="Icons.iconLogo" />
        </div>
        <div class="nav-btn flex-row">
          <div class="nav-left" :class="{enabled: navHasPre}">
            <div class="icon" :style="imgBg(Icons.arrow3)"></div>
          </div>
          <div class="nav-right" :class="{enabled: navHasNext}">
            <div class="icon" :style="imgBg(Icons.arrow2)"></div>
          </div>
        </div>
        <div class="search-box flex-row">
          <div class="icon icon-search" :style="imgBg(Icons.iconSearch)"></div>
          <input type="text">
        </div>
      </div>

      <div class="right flex-row flex-center">
        <div class="download">
          <div class="download-state">下载暂停</div>
          <div class="icon-download-box">
            <div class="icon" :style="imgBg(Icons.arrow1)"></div>
          </div>
        </div>
        <div class="mail">
          <div class="icon-mail">
            <div class="icon" :style="imgBg(Icons.iconMail)"></div>
          </div>
          <div class="counts">2</div>
        </div>
        <div class="btn-setting">
          <div class="icon" :style="imgBg(Icons.iconSetting)"></div>
        </div>
        <div class="user-info">
          <div class="flex-middle">
            <div class="icon-user" :style="imgBg(userIconUrl)"></div>
          </div>
          <div class="flex-middle">
            <div class="icon" :style="imgBg(Icons.arrow4)"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Icons from '../assets/Image/index.js'

  export default {
    name: 'Header',
    data () {
      return {
        Icons,
        userIconUrl: Icons.scene
      }
    },
    computed: {
      navHasPre () {
        return true
      },
      navHasNext () {
        return false
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

  .header {
    flex-shrink: 0;
    width: 100%;
    height: 75px;
    background-color: @theme-color;
    padding: 8px;
    padding-top: 4px;
    padding-bottom: 4px;

    color: white;
  }
  .window-btns {
    width: 100%;

    .left {
      div {
        display: flex;
        border-radius: 50%;
        height: 12px;
        width: 12px;
        cursor: pointer;
        margin-right: 8px;
        font-size: 8px;

        &:hover {
          color: #444;
        }
      }
    }
    .btn-close {
      background-color: #FF564F;
      color: #FF564F;
    }
    .btn-min {
      background-color: #FFB429;
      color: #FFB429;
    }
    .btn-max {
      background-color: #24C339;
      color: #24C339;
    }
  }

  .content {
    display: flex;
    align-items: center;

    .logo {
      width: 180px;
      margin-right: 50px;

      img {
        width: 100%;
      }
    }
    .nav-btn {
      .icon {
        display: inline-block;
        height: 20px;
        width:  20px;
        background-position: center;
        background-repeat: no-repeat;
        background-size: contain;
      }
      .nav-left,
      .nav-right {
        border: 1px solid rgba(66,66,66,0.3);
        height: 26px;
        width: 26px;
        display: flex;
        align-items: center;
        justify-content: center;

        &.enabled {
          background-color: #BE2607;
        }
      }
    }
    .search-box {
      margin-left: 5px;
      height: 26px;
      border-radius: 26px/2;
      background-color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 5px;
      padding-right: 10px;
      width: 200px;

      .icon-search {
        display: inline-block;
        flex-shrink: 0;
        height: 16px;
        width: 16px;
        background-size: contain;
        background-position: center;
        background-repeat: no-repeat;
      }
      input {
        padding: 0 4px;
        height: 100%;
        flex: 1;
        outline: none;
      }
    }

    .right {
      .download {
        margin-right: 20px;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        font-size: 14px;

        .icon-download-box {
          background-color: #801A00;
          border-radius: 50%;
          height: 20px;
          width: 20px;
          display: flex;
          align-items: center;
          justify-content: center;
          margin-left: 5px;
        }
        .icon {
          display: inline-block;
          height: 12px;
          width: 12px;
          background-position: center;
          background-repeat: no-repeat;
          background-size: contain;
        }
      }
      .mail {
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        margin-right: 20px;
        padding-top: 5px;

        .icon {
          display: inline-block;
          height: 20px;
          width:  20px;
          background-position: center;
          background-repeat: no-repeat;
          background-size: contain;
        }
        .counts {
          position: absolute;
          top: -2px;
          right: -7px;
          display: flex;
          align-content: center;
          justify-content: center;
          background-color: white;
          color: @theme-color;
          font-size: 12px;
          width: 15px;
          height: 15px;
          border-radius: 15px/2;
        }
      }
      .btn-setting {
        margin-right: 20px;

        display: flex;
        align-items: center;
        justify-content: center;

        .icon {
          display: inline-block;
          height: 20px;
          width:  20px;
          background-position: center;
          background-repeat: no-repeat;
          background-size: contain;
        }
      }
      .user-info {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        padding: 0 20px;
        border-left: 1px solid rgba(33,33,33,0.3);

        .icon-user {
          display: inline-block;
          height: 26px;
          width:  26px;
          border-radius: 50%;
          background-position: center;
          background-size: cover;
        }
        .icon {
          display: inline-block;
          height: 12px;
          width:  12px;
          background-position: center;
          background-repeat: no-repeat;
          background-size: contain;
        }
      }
    }
  }
</style>
