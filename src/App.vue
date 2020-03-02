<template>
  <div id="app">
    <div>
      <label for="name-list">输入候选人列表，使用 ',' 分隔：</label>
      <textarea v-model="nameList" ref="name-list" id="name-list" placeholder="张三,李四" />
    </div>
    <div>
      <button class="pick-btn" @click="startPick">开始抽签！</button>
    </div>
    <div v-if="pickedName">抽到的人是：{{ pickedName }}</div>
  </div>
</template>

<script>


export default {
  components: {
  },
  data() {
    return {
      pickedName: "",
      nameList: ""
    };
  },
  methods: {
    startPick() {
      let list = this.nameList.split(',');
      list = list.sort(() => {
        return Math.random() > 0.5 ? 1 : -1;
      });
      this.pickedName = list[0];
    }
  }
};
</script>

<style lang="stylus">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: column;
}
</style>
