<template>
  <a-button @click="control" :type="!on ? 'primary' : 'danger'">
    {{!on ? '开始录制' : '停止录制'}}
  </a-button>
</template>

<script>
import * as rrweb from 'rrweb'
export default {
  data() {
    return {
      on: false,
      events: [],
    }
  },
  created() {
    window.localStorage.setItem('rrweb', JSON.stringify([]))
  },
  methods: {
    control() {
      if (this.on) {
        this.on = false
        this.save()
      } else {
        this.on = true
        this.start()
      }
    },
    start() {
      this.events = []
      const _this = this
      rrweb.record({
        emit(event) {
          // 将 event 存入 events 数组中
          _this.events.push(event);
        },
      });
    },
    save() {
      const body = JSON.stringify(this.events);
      this.events = [];
      window.localStorage.setItem('rrweb', body)
    }
  }
}
</script>

<style>

</style>