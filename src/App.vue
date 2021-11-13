<template>
  <div id="app">
    <Board>
      <div class="title">
        Tic Tac Toe
      </div>
    </Board>
  </div>
</template>

<script>
import Board from './components/Board.vue'

export default {
  name: 'App',
  components: {
    Board
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  display: flex;
  width: 100vw;
 height: 100vh;
 justify-content: center;
  align-items: center;
  background-color: black; 
}
body{
  padding: 0;
  margin: 0;
}
.title{
  font-size: 2em;
  margin-bottom: 0.5em;
  font-family: 'Fira Code';
  color: #d2d2d2;
}
</style>
