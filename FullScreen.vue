<template>
  <a-tooltip :title="title" :getPopupContainer="getPopupContainer">
    <a-icon :type="icon" class="fullscreen" :style="iconStyle" @click="toggleFullScreen(targetEle)" />
  </a-tooltip>
</template>

<script>
export default {
  name: 'FullScreen',
  data () {
    return {
      icon: 'fullscreen',
      title: '全屏',
    }
  },
  props: {
    iconStyle: {
      type: Object,
      default: function () {
        return {}
      },
    },
    targetEle: {
      type: [Object, HTMLElement],
      default: function () {
        return {}
      }
    }
  },
  methods: {
    toggleFullScreen (ele) {
      if (Object.keys(ele).length === 0) {
        ele = document.getElementById('blankLayout') || document.documentElement
      }
      console.log('fullscreen', ele)
      if (!document.fullscreenElement) {
        ele.requestFullscreen()
        this.icon = 'fullscreen-exit'
        this.title = '退出全屏'
      } else {
        if (document.exitFullscreen) {
          document.exitFullscreen()
          this.icon = 'fullscreen'
          this.title = '全屏'
        }
      }
    },
    getPopupContainer (trigger) {
      return trigger.parentElement
    },
  }
}
</script>

<style scoped>
.fullscreen {
  font-size: 20px;
  margin: auto 8px;
  padding: 2px;
}
</style>
