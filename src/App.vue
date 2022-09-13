<template>
  <div class="container">
    <!-- <Header /> -->
    <Header title="Tasks Tracker" />
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    // DELETE TASKS
    deleteTask(id) {
      // console.log('task', id)
      if (confirm('You want to delete this?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    // TOGGLE REMINDER
    toggleReminder(id) {
      // console.log(id)
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Learn VueJS Crash Course',
        day: 'Sept. 12th at 1:00PM',
        reminder: true,
      },
      {
        id: 2,
        text: 'Meeting at Google Meet',
        day: 'Sept. 13th at 5:00PM',
        reminder: false,
      },
      {
        id: 3,
        text: 'Create Tasks Tracker using VueJS',
        day: 'Sept. 13th at 1:30PM',
        reminder: false,
      },
    ]
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Roboto', sans-serif;
  background-color: gray;
}

/* a {
  color: mediumaquamarine;
  text-decoration: none;
} */

/* a:hover {
  opacity: 0.8;
} */

.container {
  background-color: rgb(38, 38, 38);
  color: ivory;
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 3px solid azure;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: black;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:hover {
  opacity: 0.8;
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

/* .add-form {
  border-top: 3px solid gray;
  border-bottom: 3px solid gray;
  margin-bottom: 27px;
  padding-bottom: 22px;
} */

/* .form-control {
  margin: 20px 0;
} */

/* .form-control label {
  display: block;
} */

/* .form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
} */

/* .form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
} */

/* .form-control-check label {
  flex: 1;
} */

/* .form-control-check input {
  flex: 2;
  height: 20px;
} */

/* footer {
  margin-top: 30px;
  text-align: center;
} */
</style>
