<template>
  <div class="app">
    <p>{{ name }} - {{ age }}</p>
    <p> {{ jobs[0].title }}</p>
    <button @click="changeName('zelda')">change Name</button>
    <button @click="changeAge(25)">change Name</button>
  </div>
</template>

<script lang="ts">// lang=tsが必要
import { defineComponent, reactive, toRefs, ref } from 'vue'; // ts と連研するために必要
import Job  from './types/Job'
export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    // const state = reactive({
    //   name: 'Link',
    //   age: 25 as string|number,
    // })
    
    // // toRefs: reactive オブジェクトを ref オブジェクトに変換して返す
    // console.log('@@@@@', toRefs(state))
    // return {...toRefs(state)} 

    // const name = ref('Link')
    // const age = ref<string | number>(25) // refの方を定義する場合：Genericを使う
    // return {name, age}
    const jobs = ref<Job[]>([
      {title: 'farm', location: 'hoge', salary: 20000, id: '1'},
    ])
    return { jobs }
  },
  // data() {
  //   return {
  //     name: 'Link',
  //     age: 45 as number|string // data関数で明示的に型を指定する場合の記述
  //   }
  // },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
