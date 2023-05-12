<template>
  <div class="app">  
      <header>
        <div class="title">
          <img src="./assets/heart.svg" alt="site logo">
          <h1>Sodlcs Jobs</h1>
        </div>
        <div class="order">
          <button @click= "handleClick('title')" >Order by Title</button>  
          <button @click="handleClick('location')" >Order by Location</button>  
          <button @click="handleClick('salary')">Order by Salary</button>  
        </div>
      </header>  

      <JobList :jobs="jobs" :order="order"/>
    </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue'
import type Job from './types/Job';
import type OrderTerm  from './types/OrderTerm';
import JobList from './components/JobList.vue';

export default defineComponent({
    components:{
      JobList,
    },
    setup() {
      const jobs = ref<Job[]>([
        { title: 'Engineer', location: 'Las Vegas', salary: 160000, id: '1' },
        { title: 'Os Manager', location: 'Lake Tahoe', salary: 110000, id: '2' },
        { title: 'Project Manager', location: 'Sacramento', salary: 130000, id: '3' },
        { title: 'Actor', location: 'San Francisco', salary: 140000, id: '4' },
        { title: 'Nurse', location: 'Oakland', salary: 100000, id: '5' }
      ]);
      const order = ref<OrderTerm>('title');
      const handleClick = (term: OrderTerm ) => {
        order.value = term;
      };
      return {jobs, handleClick, order}
    }
})
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
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
  
</style>
