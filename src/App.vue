<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job'
import JobList from './components/JobList.vue';
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: {
    JobList
  },
  setup() {
    // const state = reactive({
    //   name: 'Link',
    //   age: 25 as string | number
    // })

    // state.name = "999" //cannot change type
    // state.age = '26'

    // const name = ref("Link")
    // const age = ref<number | string>("25")
    const jobs = ref<Job[]>([
      {
        id: '1',
        salary: 500,
        location: 'a loc',
        title: 'title 1'
      },
      {
        id: '2',
        salary: 300,
        location: 'b loc',
        title: 'title 2'
      },
    ])

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    };

    return { jobs, handleClick, order }
  },
  // methods: {
  //   changeName(name: string) {
  //     this.name = name
  //   },
  //   changeAge(age: number | string) {
  //     this.age = age
  //   }
  // }
});
</script>

<style scoped>
header {
  text-align: center;
}

header .order {
  margin-top: 20px;
}

button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

header .title {
  display: flex;
  justify-content: center;
}

header img {
  width: 60px;
  margin-right: 20px;
}

header h1 {
  font-size: 3em;
}</style>
