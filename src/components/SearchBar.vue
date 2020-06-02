<template>
  <div>
    <label style="font-weight: bold;">
      Filter tasks (by name)
      <div class="fg">
        <input type="text" v-model="term" @input="notifyTermChanged" @keyup.esc="clearTearm" />
        <button type="button" @click="clearTearm">Clear</button>
      </div>
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      term: ''
    };
  },
  methods: {
    notifyTermChanged() {
      const args = {
        term: this.term
      };
      this.$emit('searchTermChanged', args);
    },
    clearTearm() {
      this.term = '';
      this.notifyTermChanged();
    }
  }
};
</script>

<style scoped>
</style>