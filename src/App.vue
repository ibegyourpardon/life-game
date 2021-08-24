<template>
  <div class="container">
    <h1>L G</h1>
    <div>  {{ block_list }}  </div>
    <div
      :style="grid_container"
    >
      <div v-for="(grid, idx) in block_list" v-bind:key="idx" v-bind:style="grid || newbg" v-on:click="changebgcolor" class="grid" :id="idx"></div>

    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      rows: 15,
      styling: '  grid-template-columns: repeat(10, 10%);'
    }
  },
  computed: {
    block_list: function (){
      let x = this.rows * this.rows
      return x
    },
    grid_container: function (){
      let a = {}
      let v = (1 / this.rows) * 100
      console.log(v)
      let border = 'repeat(' + this.rows + ', ' + v +'%)'
      a.width = '800px'
      a.height = '800px'
      a.display = 'grid'
      // a.backgroundColor = 'red'
      // a.gridTemplateColumns= 'repeat(3, 33.33%)'
      a.gridTemplateColumns= border
      a.gridTemplateRows=border

      return a
    }
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
}

.container {
  margin-left: 100px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
}

.grid-container {
  /*display: flex;*/
  /*flex-direction: row;*/
  /*justify-content: flex-start;*/
  /*flex-wrap: wrap;*/
  /*align-items: flex-start;*/
  display: grid;
  /*grid-template-columns: repeat(10, 10%);*/
}

.grid {
  width: 40px;
  height: 40px;
  background-color: #42b983;
  margin: 0 2px 2px 0;
}
</style>
