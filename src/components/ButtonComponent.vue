<template>
    <button @click="Clicked" :style="{ background: color }">{{ text }}</button>        
</template>


<script>
    export default{
        props:{
            text:String,
            color:String
        },
        methods:{
            Clicked(){
                this.$emit('toggle-add-task')
            }
        }


    }


</script>

<style>
button{

    color: white;
    border: none;
    border-radius: 4px;
    padding: 10px 15px;
    cursor: pointer;
    margin-bottom: 5px;
}
</style>