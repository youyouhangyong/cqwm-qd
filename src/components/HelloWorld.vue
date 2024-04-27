<template>
  <div class="hello">
    {{ name }}
    {{ age
      ? '年龄' + age
      : '年龄未知'
    }}
    <!-- 双向绑定 -->
    <div>
      <input type="text" v-model="name">
      <input type="text" v-model="age">
    </div>
    <div>
      <img :src="src" width="25">
      <input type="text" :value="name">
      <input type="text" v-bind:value="age">
    </div>
    <div>
      <input type="button" value="保存" @click="handleSave">
    </div>
    <input type= "button" value="发送请求" @click="handleSend">
  </div>
</template>
<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      name: 'zc',
      age: 18,
      src: 'https://s11.ax1x.com/2023/05/21/p95vJyj.png'
    }
  },
  methods: {
    handleSave() {
      this.name = 'yyhy'
    },
    handleSend() {
      axios.post('http://localhost:8080/api/user/login', {
        name: 'zc',
        password: 123345
      }).then(res => {
        console.log(res.data)
      }).catch(err => {
        console.log(err)
      })
    }
  }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
