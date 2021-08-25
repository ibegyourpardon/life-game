<template>
  <div class="container">
    <h1>L G</h1>
    <!-- <div>  {{ block_list }}  </div> -->
    <div>
      <input type="number" v-model="height"/>
      <button @click="initBlockList">confirm</button>
      <button @click="runGame">start</button>
      <button @click="stopGame">stop</button>
    </div>
    <div class="block_container">
      <div v-for="(grid, idx) in block_list" v-bind:key="idx" class="block" v-bind:class="{ active: grid.active }" @click="changeColor(idx)"></div>

    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  methods: {
    initBlockList: function() {
      this.block_list = [];
      for (var i = 0; i < this.width * this.height; i++) {
        this.block_list.push({
          active: false,
        });
      }
    },
    changeColor: function(idx) {
      console.log(idx)
      this.block_list[idx].active = !this.block_list[idx].active;
    },
    runGame: function() {
      console.log('runGame')
    },
    stopGame: function() {
      console.log('stop')
    }
  },
  mounted: function() {
    this.initBlockList();
  },
  data() {
    return {
      width: 22,
      height: 10,
      block_list: []
    }
  },
  computed: {
    // block_list: function (){
    //   let x = this.width * this.height
    //   return x
    // }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  background-color: antiquewhite;
  width: 100%;
  min-height: 100vh;
}

.container {
  margin-left: 100px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
}

.block_container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: space-between;
  width: 80vw;
}

.block {
  width: 3vw;
  height: 3vw;
  background: #fff;
  margin: 0 0.5vw 0.5vw 0;
}

.active {
  background: #e74c3c;
}
</style>
