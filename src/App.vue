<template>
  <div class="container">
    <Header @toggle-task-form="toggleTaskForm" title="Task Tracker"  :isShowTaskForm="showTaskForm"/>
    <div v-show="showTaskForm">
      <AddTask @add-task="addTask"/>
    </div>
    <Tasks @toggle-remind="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>
  import Header from './components/Header.vue'
  import Tasks from './components/Tasks'
  import AddTask from './components/AddTask'

  export default {
    name: 'App',
    components: {
      Header,
      Tasks,
      AddTask
    },
    data() {
      return {
        tasks: [],
        showTaskForm: false
      }
    },
    methods: {
      toggleTaskForm() {
        this.showTaskForm = !this.showTaskForm
      },
      addTask(task) {
        this.tasks = [...this.tasks, task]
      },
      deleteTask(id) {
        if (confirm('Are You Sure to Delete this task?')) {
          this.tasks = this.tasks.filter((task) => task.id !== id)
        }
      },
      toggleReminder(id) {
        this.tasks = this.tasks.map((task) => task.id == id ? {...task, reminder: !task.reminder} : task)
      }
    },
    created() {
      this.tasks = [
        {
          id: 1,
          text: 'Create Tasks Components',
          date: 'Today at 10:50PM',
          reminder: true
        },
        {
          id: 2,
          text: 'Create Task Components for Loop in tasks',
          date: 'Today at 10:50PM',
          reminder: false
        },
        {
          id: 3,
          text: 'Check Reminder',
          date: 'Today at 10:50PM',
          reminder: false
        }
      ]
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: 'Poppins', sans-serif;
    margin: 0 10px;
  }

  .container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }

  .btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
  }

  .btn:focus {
    outline: none;
  }

  .btn:active {
    transform: scale(0.98);
  }

  .btn-block {
    display: block;
    width: 100%;
  }
</style>