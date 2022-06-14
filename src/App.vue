<template>
 <div class="app">
   <header>
     <div class="order">
    <button @click="handleClick('title')">order by Title</button>
    <button @click="handleClick('salary')">order By Salary</button>
    <button @click="handleClick('location')">order By location</button>
     </div>
   </header>
  
   <JobList :jobs="jobs" :order="order"/>
 </div>
</template>

<script lang="ts">
import { defineComponent,ref } from 'vue';
import JobList from './components/JobsList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'
export default defineComponent({
  name:'App',
  components:{
   JobList,
  },
  setup(){
     const jobs = ref<Job[]>([
       {
         title:'Fornt End Developer', location:'Noida',
         salary:30000 , id: '1'
       },
       {
         title:'Back End Developer', location:'Delhi',
         salary:40000 , id: '2'
       },
        {
         title:'Full Stack Developer', location:'Gurugram',
         salary:50000 , id: '3'
       },
       {
         title:'DevOps', location: 'Delhi',
         salary: 60000, id: '4'
       }
     ])
     const order = ref<OrderTerm>('title')
     const handleClick =  (term: OrderTerm)=>{
       order.value = term
     }
     return {jobs, handleClick,order}
  }
})

  
</script>

<style>

</style>
