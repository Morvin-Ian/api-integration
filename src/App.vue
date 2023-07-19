<template > 
  <div class="container">
    <Header @toggle-add-task="showAddTask=!showAddTask" :showAddTask="showAddTask" title="Task Tracker"/>
    <div v-show="showAddTask">
      <AddTask @new-task="addTask"/>
    </div>
    <Tasks @change-reminder="toggleReminder"  @delete-task="removeTask" :tasks="tasks" />
  </div>
</template>




<script>
import Header from './components/HeaderComponent.vue'
import Tasks from './components/AllTasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header, 
    Tasks,
    AddTask
  },

  data(){
    return{
      tasks : [],
      showAddTask:false
    }
  }, 

  methods:{
    async removeTask(id){
      const response = await fetch(`http://localhost:5000/tasks/${id}`,
      {
        method:'DELETE',
        headers:{
          'Content-type':'application/json'
        },

      })

      response.status === 200 ? (this.tasks = this.tasks.filter((task)=> task.id !== id)) : alert("Error Occured while deleting")

      
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) =>
        task.id === id ? {...task, reminder:!task.reminder} : task
      )
    },
    async addTask(task){
      const response = await fetch("http://localhost:5000/tasks",
      {
        method:'POST',
        headers:{
          'Content-type':'application/json'
        },

        body:JSON.stringify(task)

      })
      const data = await response.json()

      this.tasks = [...this.tasks,data ]
    },
     fetchTasks: async ()=> {

      const response =  await fetch("http://localhost:5000/tasks");
      const data = await response.json()
      return data

    },
    fetchTask: async (id)=> {

      const response =  await fetch(`http://localhost:5000/tasks/${id}`);
      const data = await response.json()
      return data

    }
  },


  async created(){
    this.tasks = await this.fetchTasks()
     
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
