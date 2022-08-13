<template>
  <div class="job-list">
    <p>orderd by {{order}}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2> {{ job.title}} - {{ job.location}}</h2>
        <div class="salary">
          <p>{{ job.salary}} rupees</p>
        </div>
        <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ad maiores natus nisi sint totam, aliquid fugiat, omnis provident obcaecati corporis praesentium eligendi reiciendis magni itaque est rerum culpa exercitationem amet!</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">// lang=tsが必要
import { defineComponent, PropType, computed } from 'vue'; // ts と連研するために必要
import Job from '@/types/Job'
import OrderTerm from '../types/OrderTerm';

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },
  setup(props) {
    const orderedJobs = computed(() => {
      //並べ替え. 
      // propの中身を変えないように新しく変数を生成して返す
      // sortの中で, orderで指定した属性の降順で並べるように指定
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })

    return {orderedJobs}
  }
})
</script>

<style scoped>
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0;
  }
  .job-list li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px
  }
  .salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
  }
</style>