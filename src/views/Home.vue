<template>
  <AddTask v-show="showAddTask" @add-task="addTask" />
  <Tasks
    @toggle-reminder="toggleReminder"
    @delete-task="deleteTask"
    :tasks="tasks"
  />
</template>

<script>
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'
export default {
  name: 'Home',
  props: {
    showAddTask: Boolean,
  },
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    // ADD TASK
    async addTask(task) {
      const res = await fetch('api/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(task),
      })
      const data = await res.json()
      this.tasks = [...this.tasks, data]
    },
    // DELETE TASKS
    async deleteTask(id) {
      // console.log('task', id)
      if (confirm('You want to delete this?')) {
        const res = await fetch(`api/tasks/${id}`, {
          method: 'DELETE',
        })
        res.status === 200
          ? (this.tasks = this.tasks.filter((task) => task.id !== id))
          : alert('Error Deleting Task')
      }
    },
    // TOGGLE REMINDER
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id)
      const updTask = { ...taskToToggle, reminder: !taskToToggle.reminder }
      const res = await fetch(`api/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updTask),
      })
      const data = await res.json()
      // console.log(id)
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      )
    },
    async fetchTasks() {
      const res = await fetch('api/tasks')
      const data = await res.json()
      return data
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`)
      const data = await res.json()
      return data
    },
  },
  // created() {
  //   this.tasks = [
  //     {
  //       id: 1,
  //       text: 'Learn VueJS Crash Course',
  //       day: 'Sept. 12th at 1:00PM',
  //       reminder: true,
  //     },
  //     {
  //       id: 2,
  //       text: 'Meeting at Google Meet',
  //       day: 'Sept. 13th at 5:00PM',
  //       reminder: false,
  //     },
  //     {
  //       id: 3,
  //       text: 'Create Tasks Tracker using VueJS',
  //       day: 'Sept. 13th at 1:30PM',
  //       reminder: false,
  //     },
  //   ]
  // },
  async created() {
    this.tasks = await this.fetchTasks()
  },
}
</script>
