<template > 
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks @change-reminder="toggleReminder"  @delete-task="removeTask" :tasks="tasks" />
  </div>
</template>




<script>
import Header from './components/HeaderComponent.vue'
import Tasks from './components/AllTasks.vue'

export default {
  name: 'App',
  components: {
    Header, 
    Tasks
  },

  data(){
    return{
      tasks : []
    }
  }, 

  methods:{
    removeTask(id){
      this.tasks = this.tasks.filter((task)=> task.id !== id)
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) =>
        task.id === id ? {...task, reminder:!task.reminder} : task
      )
    }
  },


  created(){
    this.tasks = [
      {
        id:1, 
        text:"JavaScript Coding",
        date:"March 11th at 9 am",
        reminder:true
      },
      {
        id:2, 
        text:"UFC Fights",
        date:"March 17th at 11 pm",
        reminder:true
      },
      {
        id:3, 
        text:"Golf course",
        date:"April 11th at 12 noon",
        reminder:false
      }
    ]
  },
}
</script>

<style scoped>

.container{
    border: 1px solid rgb(0, 163, 184);
    padding: 10px;
    border-radius: 4px;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;

}


</style>
