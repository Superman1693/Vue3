<script setup>
import { ref, reactive, toRef, toRefs } from "vue";
const sb = 'Hello';
let a = ref(1);
const b = '<h1>6666666682829</h1>';
const message = 'Hello Vue!'
const sum = () => {
  a.value++;
}
const active = ref('active');
const obj = [{
  name: 'zhangsan',
  age: 18
},
];
const obj2 = reactive({ address: 'beijing', age: 18 });
const obj3 = toRef(obj2, 'address');
setTimeout(() => {
  obj3.value = 'xiamen';


}, 2000);
const obj4 = toRefs(obj2);
setTimeout(() => {
  obj4.age.value = 109;
}, 2000);
let second = ref(new Date().getSeconds())
let year = ref(new Date().getFullYear())
let month = ref(new Date().getMonth() + 1)
let day = ref(new Date().getDate())
let hour = ref(new Date().getHours())
let minute = ref(new Date().getMinutes())

let years = setInterval(() => {
  second.value = new Date().getSeconds();
  year.value = new Date().getFullYear();
  month.value = new Date().getMonth() + 1;
  day.value = new Date().getDate();
  hour.value = new Date().getHours();
  minute.value = new Date().getMinutes();
}, 1000)
setTimeout(() => {
  clearInterval(years);
}, 5000)
const number = '请输入分数';
let fun = ref();

</script>

<template>
  <h1>{{ year }}-{{ month }}-{{ day }} {{ hour }}:{{ minute }}:{{ second }}</h1>
  <div>
    <h1>{{ sb }}</h1>
  </div>
  <button @click="sum">{{ a }}</button>
  <ul>
    <li v-for="(item, index) in obj">{{ item.name }}</li>
  </ul>
  <div>地址：{{ obj2.address }}</div>
  <div>地址：{{ obj3 }}</div>
  <div>
    <ul>
      <li>{{ obj4.address }}</li>
      <li>{{ obj4.age }}</li>
    </ul>
  </div>
  <ul>
    <li v-text="sb"></li>
    <li v-html="b"></li>
  </ul>

  <div v-pre>{{ message }}</div>
  <div :class="[active]">{{ message }}</div>
  <input type="text" v-model.number.lazy="fun">
  <p> <span v-if="fun >= 95">刘星的成绩优秀</span><span v-else-if="fun >= 75">刘星的成绩良好</span><span
      v-else-if="fun >= 60">刘星的成绩及格</span><span v-else-if="fun < 60">刘星的成绩不及格</span></p>
  <h1>成绩表</h1>
  <ul>
    <li></li>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
  </ul>
</template>

<style>
.active {
  color: red;
}
</style>
