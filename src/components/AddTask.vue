<template>
    <form class="form" @submit="submitTask">
       <div class="input">
        <label for="name">Add Task </label> <br>
        <input id="add" type="text" v-model="task" placeholder="Add Task"> <br>
       </div>

       <div class="input">
        <label for="name">Day & Time </label> <br>
        <input type="text" v-model="date" id="add1" placeholder="Add Day and Time"> <br>
       </div>

       <div class="input">
        <label for="name">Reminder </label> <br>
        <input type="checkbox" v-model="reminder" name="" id="check"> 
       </div>
      
        <Button text="Save Task" color="black"/>
        
    </form>
</template>

<script>
    import Button from './ButtonComponent.vue'

    export default{
        data(){
            return {
                task:'',
                date:'',
                reminder:false
            }
        },
        components:{
            Button
        },
        methods:{
            submitTask(e){
                e.preventDefault();
                
                if(!this.task){
                    alert("Task input must be filled")
                    return
                }

                const newTask = {
                    id:Math.floor(Math.random()*100000),
                    text:this.task,
                    date:this.date,
                    reminder:this.reminder
                }

                this.$emit('new-task', newTask)

                this.task = ''
                this.date = ''
                this.reminder = false

            }
        }
    }
</script>

<style scoped>
.form{
    margin: 10px;
}

.input{
    margin: 10px;
}

.input #add, #add1{
    padding: 10px;
    width: 100%;
    margin-top: 4px;
}


</style>