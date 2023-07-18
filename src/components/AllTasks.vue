<template>
    <div v-for="task in tasks" :key="task.id">
        <Task @change-reminder="$emit('change-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task"/>
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
        },
        emits:['delete-task', 'change-reminder']

    }
</script>