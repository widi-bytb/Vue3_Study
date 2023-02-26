<template>
  <h4>当前求和为：{{sum}}</h4>
  <button @click="sum++">点我x+1</button>
  <hr>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪资：{{salary}}K</h2>
  <h3 v-show="person.car">座驾信息:{{person.car}}</h3>
  <button @click="name+='大'">修改名字</button>
  <button @click="age++">修改年龄</button>
  <button @click="salary++">涨薪</button>
  <button @click="showRawPerson">输出最原始的person</button>
  <button @click="addCar">给人添加一台车</button>
  <button @click="person.car.name+='!'">换车名</button>
  <button @click="changePrice">换价格</button>
</template>

<script>
import {reactive, toRefs, ref, toRaw ,markRaw } from "vue";
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
    function showRawPerson(){
      // const p = toRaw(person)
      // console.log(p)

      // const s = toRaw(sum)
      // console.log(s)
    }

    function addCar(){
      let car = {name:'奔驰',price:40}
      person.car = markRaw(car)
    }

    function changePrice(){
      person.car.price++
      console.log(person.car.price)
    }

    return {
        sum,
      person,
      changePrice,
      showRawPerson,
      addCar,
      ...toRefs(person),
      ...toRefs(person.job.j1)
    }
  }
}
</script>

<style scoped>

</style>
