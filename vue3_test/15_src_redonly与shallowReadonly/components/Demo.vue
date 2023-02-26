<template>
  <h4>当前求和为：{{sum}}</h4>
  <button @click="sum++">点我x+1</button>
  <hr>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪资：{{salary}}</h2>
  <button @click="name+='大'">修改名字</button>
  <button @click="age++">修改年龄</button>
  <button @click="salary++">涨薪</button>
</template>

<script>
import {reactive, toRefs, ref, readonly, shallowReadonly} from "vue";
export default {
  name: "Demo",
  setup() {
    //数据
    let sum = ref(0)
    let person = reactive({
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })

    // person = readonly(person)
    person = shallowReadonly(person)

    return {
        sum,
      ...toRefs(person),
      ...toRefs(person.job.j1)
    }
  }
}
</script>

<style scoped>

</style>
