<template>
    <div class="board">
      <div class="row" v-for="rowIndex in 3" :key="rowIndex">
        <div class="cell" v-for="colIndex in 3" :key="colIndex" @click="handleClick((rowIndex - 1) * 3 + colIndex - 1)">
          <span>{{ cells[(rowIndex - 1) * 3 + colIndex - 1] }}</span>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "TicTacToeBoard",
    props: {
      cells: Array,
    },
    methods: {
      handleClick(index) {
        this.$emit("cell-clicked", index);
      },
    },
  };
  </script>
  
  <style scoped>
  .board {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 300px;
    height: 300px;
    margin: 0 auto;
  }
  
  .row {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    background-color: #4777a2 ;
  }
  
  .cell {
    width: 100px;
    height: 100px;
    border: 1px solid #d8deff;
    display: flex;
    justify-content: center;
    align-items: center;
    
  }
  
  .cell span {
    font-size: 50px;
    font-family: Roboto, sans-serif;
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.2);
  }
  
  
  </style>
  