<template>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪资：{{salary}}</h2>
  <button @click="name+='大'">修改名字</button>
  <button @click="age++">修改年龄</button>
  <button @click="salary++">涨薪</button>
</template>

<script>
import {reactive,toRef,toRefs} from "vue";
export default {
  name: "Demo",
  setup() {
    //数据
    let person = reactive({
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })

    // const name = toRef(person,'name')
    // console.log(name)

    const x = toRefs(person)
    console.log('xxx',x)
    return {
      person,
     // name:toRef(person,'name'),
     //  age:toRef(person,'age'),
     //  salary: toRef(person.job.j1,'salary')
      ...toRefs(person),
      ...toRefs(person.job.j1)
    }


  }
}
</script>

<style scoped>

</style>
