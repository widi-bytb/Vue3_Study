<template>
  <h1>一个人的信息</h1>
  <h2 v-show="person.name">姓名：{{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <button @click="test">测试触发一下Demo组件的hello事件</button>
  <slot name="qwe"></slot>
</template>

<script>
import {reactive} from "vue";
export default {
  name: "Demo",
  props:['msg','school'],
  emits:['hello'],
  setup(props,context) {
    console.log('--setup--',props,context)
    // 数据
    let person = reactive({
      name: '张三',
      age: 18,
    })

    function test(){
      context.emit('hello',666)
    }


    return {
      person,
      test
    }


  }
}
</script>

<style scoped>

</style>
