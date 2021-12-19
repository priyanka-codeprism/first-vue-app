<template>
  <div class="container">
    <Nav
      title="Task Tracker"
      @toogle-add-task="toogleAddTask"
      :showAddTask="showAddTask"
    />
    <!-- <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Task
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    /> -->
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer/>
  </div>
</template>

<script>
import Footer from './components/Footer.vue'
//import Header from './components/Header.vue'
import Nav from "./components/Nav.vue";
export default {
  name: "App",
  components: {
    Nav,
     Footer
  },
  data() {
    return {
      showAddTask: false,
    };
  },
  methods: {
    toogleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  
  },
  
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  padding: 20px;
  border: 1px solid black;
  max-width: 500px;
  margin: auto;
}
</style>
