<template>
  <div>
    <h3>Add Task</h3>
    <div class="fg">
      <input type="text" v-model="taskName" @keyup.enter="handleClick" />
      <button type="button" @click="handleClick">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      taskName: ''
    };
  },
  methods: {
    handleClick() {
      const args = {
        id: Math.floor(Math.random() * 100) + 1,
        name: this.taskName,
        isDone: false
      };
      this.$emit('taskAdded', args);
      this.taskName = '';
    }
  }
};
</script>

<style scoped>
</style>