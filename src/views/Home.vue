 <template>
     <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Task
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    /> 
 </template>
 <script>
import Task from '../components/Task.vue'
import AddTask from '../components/AddTask.vue'
export default {
    name:'Home',
    props:{
        showAddTask:Boolean,
    },
    components:{
        AddTask, Task
    },
    data(){
        return{
             tasks: [],
        }
    },
    methods: {
    async deleteTask(id) {
      console.log("clicked");
      if (confirm("Are you sure ?")) {
        const res = await fetch(`http://localhost:5000/tasks/${id}`, {
          method: "DELETE",
        });
        res.status === 200
          ? (this.tasks = this.tasks.filter((e) => e.id !== id))
          : alert("Error deleting");
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    async addTask(task) {
      const res = await fetch("http://localhost:5000/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await res.json();
      this.tasks = [...this.tasks, data];
    },
    async fetchTasks() {
      const res = await fetch("http://localhost:5000/tasks");
      const data = await res.json();
      return data;
    },
    //   async fetchTask(id){
    // const res=await fetch('http://localhost:5000/tasks');
    // const data= await res.json();
    // return data;
    //   }
  },
  async created() {
    this.tasks = await this.fetchTasks();
  },
}
 </script>
