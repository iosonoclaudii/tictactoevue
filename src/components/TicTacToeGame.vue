<template>
  <div>
    <h1 class="title">TicTacToe</h1>
    <TicTacToeBoard :cells="cells" @cell-clicked="handleClick" />
    <button class="reset-button" @click="resetGame">Reset Game</button>
    <div class="winner">
      <h1 v-if="winner">Il vincitore è: {{ winner }}</h1>
      <h1 v-else-if="isDraw">Pareggio!</h1>
    </div>
  </div>
</template>

<script>
import TicTacToeBoard from "./TicTacToeBoard";

export default {
  name: "TicTacToeGame",
  components: {
    TicTacToeBoard,
  },
  data() {
    return {
      turn: "X",
      cells: ["", "", "", "", "", "", "", "", ""],
      winner: null,
    };
  },
  computed: {
    isDraw() {
      return !this.cells.includes("") && !this.winner;
    },
  },
  methods: {
    resetGame() {
      this.turn = "X";
      this.cells = ["", "", "", "", "", "", "", "", ""];
      this.winner = null;
    },
    handleClick(index) {
      if (this.winner) {
        return;
      }

      if (this.cells[index] !== "") {
        return;
      }

      this.cells[index] = this.turn;

      if (this.checkWinner()) {
        this.winner = this.turn;
      } else if (!this.cells.includes("")) {
        this.winner = null;
      } else {
        this.turn = this.turn === "X" ? "O" : "X";
      }
    },
    checkWinner() {
      for (let i = 0; i < 3; i++) {
        if (
          this.cells[i] === this.cells[i + 3] &&
          this.cells[i] === this.cells[i + 6] &&
          this.cells[i] !== ""
        ) {
          return this.cells[i];
        }
      }

      for (let i = 0; i < 9; i += 3) {
        if (
          this.cells[i] === this.cells[i + 1] &&
          this.cells[i] === this.cells[i + 2] &&
          this.cells[i] !== ""
        ) {
          return this.cells[i];
        }
      }

      if (
        this.cells[0] === this.cells[4] &&
        this.cells[0] === this.cells[8] &&
        this.cells[0] !== ""
      ) {
        return this.cells[0];
      }

      if (
        this.cells[2] === this.cells[4] &&
        this.cells[2] === this.cells[6] &&
        this.cells[2] !== ""
      ) {
        return this.cells[2];
      }

      return null;
    },
  },
};
</script>

<style scoped>
.title {
  font-size: 50px;
}
.reset-button {
  margin-top: 40px;
  background-color: #4777a2;
  color: #ffffff;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.2s;
  border: none;
}

.reset-button:hover {
  background-color: #446699;
  color: #ffffff;
}

.reset-button:active {
  background-color: #5080b1;
  color: #ffffff;
}
</style>
