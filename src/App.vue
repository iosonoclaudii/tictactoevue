<template>
  <div id="app">
    <TicTacToeGame />
  </div>
</template>

<script>
import TicTacToeGame from './components/TicTacToeGame';

export default {
  name: 'App',
  components: {
    TicTacToeGame
  }
};
</script>

<style>
body {
  background-color: #d8deff;
}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
