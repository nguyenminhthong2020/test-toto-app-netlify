<template>
  <div class="container">
    <search-bar @searchTermChanged="filterTasks" />
    <!-- <tasks :list="shownTasks" /> -->
    <!--Infymt-->
    <tasks :list="shownTasks" @itemDeleted="setTaskDone" />
    <new-task @taskAdded="addTask" />
    <button @click="showTasksJson">show data</button>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import Tasks from './components/Tasks.vue';
import NewTask from './components/NewTask.vue';

export default {
  components: {
    SearchBar,
    Tasks,
    NewTask
  },
  data() {
    return {
      tasks: [],
      shownTasks: []
    };
  },
  mounted() {
    this.tasks = [
      { id: 1, name: 'Pay Bills', isDone: true },
      { id: 2, name: '@vue/cli vs create-react-app', isDone: false },
      { id: 3, name: 'vue-router vs react-router', isDone: false },
      { id: 4, name: 'redux vs vuex', isDone: false }
    ];
    this.shownTasks = [...this.tasks];
  },
  methods: {
    addTask(task) {
      this.tasks.push(task);
      this.shownTasks.push(task);
    },
    filterTasks(args) {
      const lcTerm = args.term.toLowerCase();
      this.shownTasks = this.tasks.filter(item =>
        item.name.toLowerCase().includes(lcTerm)
      );
    },
    setTaskDone(task) {
      this.tasks.map(item => {
        if (item.id === task.id) item.isDone = true;
      });
    },
    showTasksJson() {
      alert(JSON.stringify(this.tasks));
    }
  }
};
</script>

<style>
body {
  background: #fff;
  color: #333;
  font-family: Lato, sans-serif;
}

.container {
  width: 400px;
  margin: 0 auto;
  margin-top: 100px;
}

h3 {
  color: #333;
  font-weight: bold;
  font-size: 25px;
  border-bottom: 2px solid #333;
  padding: 30px 0 3px 0;
  margin: 0 0 20px;
  text-transform: uppercase;
}

button {
  border-radius: 4px;
  color: white;
  min-width: 80px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 10pt;
  cursor: pointer;
  background-color: white;
  color: black;
  border: 2px solid #008cba;
  transition-duration: 0.2s;
}

button:hover {
  background-color: #008cba;
  color: white;
}

input[type='text'] {
  display: inline-block;
  width: 100%;
  font-size: 11pt;
  -webkit-transition: all 0.3s ease-in-out;
  -moz-transition: all 0.3s ease-in-out;
  -ms-transition: all 0.3s ease-in-out;
  -o-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
  outline: none;
  padding: 7px 0px 7px 7px;
  margin: 5px 1px 3px 0px;
  border: 1px solid #dddddd;
  border-left: none;
  border-right: none;
  border-top: none;
}

input[type='text']:focus {
  box-shadow: 0 0 7px rgba(81, 203, 238, 1);
  border: 1px solid rgba(81, 203, 238, 1);
}

.fg {
  display: flex;
  justify-content: space-between;
}

.fg input {
  margin-right: 10px;
}

ul {
  margin: 0;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  list-style: none;
  border-bottom: 1px solid #eee;
  font-size: 18px;
  line-height: 40px;
  padding-left: 20px;
}

li.done {
  text-decoration: line-through;
  color: #ddd;
}
</style>
