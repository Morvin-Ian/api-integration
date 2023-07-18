<template>
    <div >
        <h2 style="text-align: center;">{{ title }}</h2>
        <Button text="Add Task" color="green"/>    
    </div>
</template>

<script>
import Button from './ButtonComponent.vue'

export default{
    props:{
        title:String
    },
    components:{
        Button

    }
}
</script>

