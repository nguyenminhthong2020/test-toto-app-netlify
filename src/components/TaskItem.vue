<template>
  <!-- <li v-bind:class="{ done: value.isDone }">
    {{value.name}}
    <button v-if="!value.isDone" @click="setDone">Delete</button>
  </li> -->
  <li v-bind:class="{ done: value.isDone }">
    {{value.name}}
    <button v-if="!value.isDone" @click="notifyItemDeleted">Delete</button>
  </li>
</template>

<script>
export default {
  props: ['value'],
  methods: {
    // setDone() {
    //   this.value.isDone = true;
    // }
    notifyItemDeleted() {
      this.$emit('itemDeleted', this.value);
    }
  }
};
</script>

<style scoped>
</style>