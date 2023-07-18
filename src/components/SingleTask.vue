<template>
    <div @click="changeReminder(task.id)" :class="[task.reminder ? 'reminder' : 'task' ]">
        <h4>{{ task.text }} <span @click="deleteTask(task.id)">X</span>  </h4>
        <p>{{ task.date }}</p>
    </div>
</template>

<script>
    export default{
        props:{
            task:Object
        },
        methods:{
            deleteTask(id){
                this.$emit('delete-task', id);
            },

            changeReminder(id){
                this.$emit('change-reminder', id)
            }

        }
        
    }
</script>

<style>
.task{
    font-size: small;
    padding: 5px 20px;
    background-color: rgba(128, 128, 128, 0.288);
    margin-top: 2px;
    border-radius: 3px;
    cursor: pointer;
}
.task span{
    float: right;
    cursor: pointer;
    color: red;
}

.reminder{
    font-size: small;
    padding: 5px 20px;
    background-color: rgba(128, 128, 128, 0.288);
    margin-top: 2px;
    border-radius: 3px;
    border-left: 4px solid green;
    cursor: pointer;
}
.reminder span{
    float: right;
    cursor: pointer;
    color: red;
}

</style>