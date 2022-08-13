<template>
  <div class="app">
    <JobList :jobs="jobs" />
  </div>
</template>

<script lang="ts">// lang=tsが必要
import { defineComponent, reactive, toRefs, ref } from 'vue'; // ts と連研するために必要
import JobList from './components/JobList.vue'
import Job  from './types/Job'
export default defineComponent({
  name: 'App',
  components: {JobList},
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
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
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
