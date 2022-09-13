<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : 'neglect', 'task']"
  >
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>

    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object,
  },
  /*
  // DELETE TASKS
  methods: {
    onDelete(id) {
      this.$emit('delete-task', id)
    },
  },
*/
}
</script>

<style scope>
.fas {
  color: firebrick;
}

.task {
  background: rgb(22, 22, 22);
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.neglect {
  border-top: 1px solid red;
  border-left: 7px solid red;
}

.task.reminder {
  border-top: 1px solid yellowgreen;
  border-left: 7px solid yellowgreen;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
