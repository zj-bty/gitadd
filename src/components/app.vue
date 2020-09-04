<template>
  <div class="hello">
    <h1 v-bind:title="hello">{{ hello }}</h1>
    <h2 v-if="seen">Essential Links</h2>
    <h2 v-show="seen">{{text}}</h2>
    <h2 :[titles]="pkh">动态绑定值</h2>
    <form>
      <input type="text" v-model="text">
      <input type="text" v-model="num1">+
      <input type="text" v-model="num2">
      <input type="text" v-model="sum">
      <input type="text" v-model="sumFn">
    </form>
    <ul>
      <li v-for="item in date" :key="item.id" @click="clickFn(item.id)">{{item.name}}</li>
    </ul>
    <div v-html="chtml"> </div>
    <foote :footers="footerDta"></foote>
  </div>
</template>

<script>
import foote from '@/core/foot'
export default {
  name: 'HelloWorld',
  components: { // 组件
    foote
  },
  data () {
    return {
      hello: 'hello Work' + new Date().toLocaleString(),
      seen: true,
      text: '显示',
      titles: 'title',
      pkh: '动态绑定值',
      num1: 0,
      num2: 0,
      sum: 0,
      footerDta: '底部版权',
      chtml: '<p>p<p>',
      date: [
        {id: 1, name: 'w文字'},
        {id: 2, name: 'n文字'}
      ]
    }
  },
  watch: {
    num1: function () {
      this.sum = Number(this.num1) + Number(this.num2)
    },
    num2: function () {
      this.sum = Number(this.num1) + Number(this.num2)
    }
  },
  computed: {// // 计算属性的 getter
    sumFn: function () {
      return (Number(this.num1) + Number(this.num2))
    }
  },
  methods: { // 方法
    clickFn: function (e) {
      this.hello = this.hello.split('').reverse().join('')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>
