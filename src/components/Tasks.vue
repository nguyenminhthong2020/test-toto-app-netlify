<template>
  <div>
    <h3>Todo</h3>
    <ul>
      <!-- <task-item v-for="item in list" :key="item.id" :value="item" /> -->
      <task-item v-for="item in list" :key="item.id" :value="item" @itemDeleted="notifyItemDeleted" />
    </ul>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue';

export default {
  props: ['list'],
  components: {
    TaskItem
  },
  methods: {
    notifyItemDeleted(task) {
      this.$emit('itemDeleted', task);
    }
  }
};
</script>

<style lang="scss" scoped>
</style>