<template>
  <div class="check">
    <div class="button" @click="changeColor">切换颜色</div>
    <Echarts :theme="theme" />
  </div>
</template>

<script>
import option from '../common/echart.js'
import Echarts from './Echarts';
export default {
  name: 'HelloWorld',
  components: {
    Echarts
  },
  data () {
    return {
      theme: 'a'
    }
  },
  methods: {
    changeColor(command){
      if (this.theme == 'a') {
        this.theme = 'b';
      }
      else {
        this.theme = 'a'
      }
      document.getElementById('app').className ='theme'+this.theme ;
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '../assets/styles/theme.less'
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.button {
  display: inline-block;
  width: 300px;
  height: 30px;
  border: 1px solid gray;
  cursor: point
}
</style>
