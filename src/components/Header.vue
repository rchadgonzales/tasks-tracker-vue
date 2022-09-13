<template>
  <header>
    <!-- <h1>Tasks Tracker</h1> -->
    <h1>{{ title }}</h1>
    <Button text="Add Task" color="blue" />
  </header>
</template>

<script>
import Button from './Button.vue'

export default {
  name: 'Header',
  // props: ['title'],
  props: {
    title: String,
    // title: {
    //   type: String,
    //   default: 'Hello World',
    // },
  },
  components: {
    Button,
  },
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
