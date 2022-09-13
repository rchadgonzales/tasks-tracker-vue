<template>
  <form class="add-form">
    <div class="form-control">
      <label>Task :</label>
      <input type="text" name="task" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day and Time :</label>
      <input type="text" name="day" placeholder="Add Day and Time" />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder :</label>
      <input type="checkbox" name="reminder" />
    </div>
    <input class="btn btn-block" type="submit" value="Save Task" />
  </form>
</template>
