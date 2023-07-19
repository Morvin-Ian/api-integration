<template>
    <div >
        <h2 style="text-align: center;">{{ title }}</h2>
        <Button @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'"/>    
    </div>
</template>

<script>
import Button from './ButtonComponent.vue'

export default{
    props:{
        title:String,
        showAddTask:Boolean
    },
    components:{
        Button

    }
}
</script>

