<template>
  <div id="app">
    <ToDoList/>
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'app',
  components: {
    ToDoList
  }
}
</script>

<style lang="scss">
body {
  position: relative;
  background-color: #f0efe9;
  padding: 0;
  margin: 0;
}

* {
  box-sizing: border-box;

  &::after,
  &::before {
    box-sizing: inherit;
  }
}

#app {
  font-family: 'GothamRounded', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 16px;
  line-height: 1.2;
  text-align: center;
  color: #3e434f;
  background-color: #fff;
  box-shadow: 0px 6px 15px 0px rgba(207, 211, 218, 0.35);
  position: relative;
  width: 420px;
  margin-top: 150px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 200px;
  padding: 50px;
}
</style>
