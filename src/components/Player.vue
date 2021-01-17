<template>
  <div >
    <a-button type="primary" @click="showModal">
      查看回放
    </a-button>
    <a-modal :width="1200" :destroyOnClose="true" v-model="visible" title="Basic Modal" @ok="handleOk">
      <div class="container" ref="player">

      </div>
    </a-modal>
  </div>
</template>
<script>
import rrwebPlayer from 'rrweb-player'
export default {
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    showModal() {
      this.visible = true;
    },
    handleOk() {
      this.visible = false;
    },
    play() {
      this.$nextTick(function () {
        new rrwebPlayer({
          target: this.$refs.player, // 可以自定义 DOM 元素
          // 配置项
          props: {
            events: JSON.parse(window.localStorage.getItem('rrweb')) || [],
          },
        });
      })
    },
  },
  watch: {
    visible: function(visible) {
      if (visible) {
        this.play()
      }
    }
  }
};
</script>
<style>
.container {
  width: 100%;
  height: 800px;
}
</style>
