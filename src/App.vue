<template>
  <div class="container">
    <!-- <Header /> -->
    <Header
      @toggle-add-task="toggleAddTask"
      title="Tasks Tracker"
      :showAddTask="showAddTask"
    />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      showAddTask: false,
    }
  },
  methods: {
    // TOGGLE ADD TASK
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
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
  background: linear-gradient(blue, rgb(54, 152, 218));
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
</style>
