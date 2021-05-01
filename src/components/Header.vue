<template>
  <header>
    <h1>{{ title }}</h1>
    <Button @toggle-task-form="$emit('toggle-task-form')" :name="isShowTaskForm ? 'Close Form' : 'Add Task'" :bg_color="isShowTaskForm ? 'red' : 'purple'" />
  </header>
</template>

<script>
  import Button from './Button';
  export default {
    name: 'Header',
    props: {
      title: String,
      isShowTaskForm: Boolean
    },
    components: {
      Button,
    }
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