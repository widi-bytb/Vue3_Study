<template>
  <h4>当前的x值是：{{x}}</h4>
  <button @click="x++">点我x+1</button>
  <hr>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪资：{{salary}}</h2>
  <button @click="name+='大'">修改名字</button>
  <button @click="age++">修改年龄</button>
  <button @click="salary++">涨薪</button>
</template>

<script>
import {reactive,toRefs,ref,shallowRef,shallowReactive} from "vue";
export default {
  name: "Demo",
  setup() {
    //数据
    // let person = shallowReactive({ //只考虑第一层数据的响应式
      let person = reactive({
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })
    let x = shallowRef(0)

    return {
        x,
      person,
      ...toRefs(person),
      ...toRefs(person.job.j1)
    }


  }
}
</script>

<style scoped>

</style>
