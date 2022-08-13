<template>
  <div class="app">
    <p>{{ name }} - {{ age }}</p>
    <button @click="changeName('zelda')">change Name</button>
    <button @click="changeAge(25)">change Name</button>
  </div>
</template>

<script lang="ts">// lang=tsが必要
import { defineComponent } from 'vue'; // ts と連研するために必要

export default defineComponent({
  name: 'App',
  components: {},
  data() {
    return {
      name: 'Link',
      age: 45 as number|string // data関数で明示的に型を指定する場合の記述
    }
  },
  methods: {
    changeName(name: string) {
      this.name = name
    },
    changeAge(age: number | string) {
      this.age = age
    },
  }
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
