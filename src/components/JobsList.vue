<template>
<div class="jobs-list">
    <p>Ordered By {{order}} </p>
    <ul>
        <li v-for="job in orderedJobs" :key="job.id">
            <h2>{{job.title}} in {{job.location}}</h2>
            <div class="salary">
                <p>{{job.salary}} rupees</p>
            </div>
            <div class="description">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Nemo ipsa veritatis saepe adipisci, repudiandae commodi incidunt! Eos, voluptates? Voluptatem non reprehenderit tenetur voluptas. Vitae corrupti qui fugiat! Cumque, repellat similique.
            </div>
        </li>
    </ul>
</div>
</template>
<script lang="ts">
import {computed,defineComponent, PropType} from 'vue'
import Job from '../types/Job'
import OrderTerm from '../types/OrderTerm'
export default defineComponent({
props: {
    jobs:{
        required: true,
        type:Array as PropType<Job[]>
    },
    order:{
        required: true,
        type: String as PropType<OrderTerm>
    }
},
setup(props){
    const orderedJobs = computed(()=>{
        return [...props.jobs].sort((a:Job,b:Job) => {
            return a[props.order] >b[props.order]? 1: -1
        })
    })
    return {orderedJobs}
}
})
</script>
<style scoped>

</style>