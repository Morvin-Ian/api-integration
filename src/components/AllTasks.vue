<template>
    <div v-for="task in tasks" :key="task.id">
        <Task :task="task"/>
    </div>

</template>

<script>
import Task from './SingleTask.vue'

    export default{
        components:{
            Task
        },

        props:{
            tasks:Array
        }
    }
</script>