<template>
  <div class="page flex-col">
    <page-header />
    <div class="flex-1 flex-row">
      <div class="flex-no-shrink">
        <page-panel />
        <play-box />
      </div>
      <page-album />
    </div>
    <page-footer />
  </div>
</template>

<script>
  import PageHeader from './Header.vue'
  import PagePanel from './Panel.vue'
  import PageFooter from './Footer.vue'
  import PageAlbum from './Album.vue'
  import PlayBox from './PlayBox.vue'

  export default {
    name: 'hello',
    data () {
      return {}
    },
    components: {
      PageHeader,
      PagePanel,
      PageFooter,
      PageAlbum,
      PlayBox
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
  @import "../less/common.less";

  .page {
    height: 100vh;
    width: 100vw;
    min-width: 860px;
    border-radius: 10px;

    .flex-no-shrink {
      display: flex;
      flex-direction: column;

      position: relative;
      flex-shrink: 0;
      width: 180px;

      .panel {
        user-select: none;
        display: inline-block;
        overflow-y: auto;
        flex: 1;
        width: 180px;
        background-color: #F5F4F5;
        border-right: 1px solid #EEE;
        flex-shrink: 0;
      }
      .play-box {

      }
    }
  }
</style>
