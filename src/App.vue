<template>
  <div ref="app" id="app">
    <HelloWorld/>
    <div class="buttons">
      <Controller></Controller>
      <Player></Player>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Player from './components/Player.vue'
import Controller from './components/Controller.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Player,
    Controller,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.buttons {
  margin-top: 80px;
  display: flex;
  justify-content: space-around;
  width: 50%;
  margin: 80px 0 0 200px;
}
</style>
