<template>
  <div>
    <div>
      <p>
        <strong>
          Criar um algoritmo que gere uma matriz 5x5 e imprima:
          <br />
          a) Toda a matriz.
          <br />
          b) A matriz gerada apenas com os números ímpares.
          <br />
          c) A matriz gerada apenas com os números pares.
        </strong>
      </p>
    </div>
    <div>
      <div class="result">
        <button class="btn" @click="answer">Gerar Matriz</button>
        <div v-if="choice == 'full'">
          <span v-if="grid[0] != ''"> {{ grid }} </span>
        </div>
        <div v-else-if="choice == 'even'">
          <span v-if="grid[0] != ''"> {{ gridEven }} </span>
        </div>
        <div v-else>
          <span v-if="grid[0] != ''"> {{ gridOdd }} </span>
        </div>
      </div>
    </div>
    <div class="inputRadio">
      <span
        ><input type="radio" value="full" v-model="choice" /> Matriz Completa
      </span>
      <span
        ><input type="radio" value="even" v-model="choice" /> Matriz Par
      </span>
      <span
        ><input type="radio" value="odd" v-model="choice" /> Matriz Ímpar
      </span>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    start() {
      this.grid = [[], [], [], [], []];
      this.gridEven = [[], [], [], [], []];
      this.gridOdd = [[], [], [], [], []];
    },
    answer() {
      this.start();
      this.getArr();
      this.getEvenOdd();
    },
    getArr() {
      for (let i = 0; i < 5; i++) {
        for (let j = 0; j < 5; j++) {
          if (this.grid[i].length < 5) {
            const random = this.getRandom();
            this.grid[i].push(random);
          }
        }
      }
    },
    getRandom() {
      const min = 1;
      const max = 25;

      return Math.floor(Math.random() * (max - min + 1)) + min;
    },
    getEvenOdd() {
      for (let i = 0; i < 5; i++) {
        for (let j = 0; j < 5; j++) {
          if (this.grid[i][j] % 2 == 0) {
            this.gridEven[i].push(this.grid[i][j]);
          } else {
            this.gridOdd[i].push(this.grid[i][j]);
          }
        }
      }
    },
  },
  data() {
    return {
      choice: "full",
      grid: [[], [], [], [], []],
      gridEven: [[], [], [], [], []],
      gridOdd: [[], [], [], [], []],
    };
  },
};
</script>

<style>
.btn {
  padding: 2px 5px;
  font-size: 1rem;
  border-radius: 5px;
  color: #fff;
  background-color: grey;
}
.result {
  display: block;
}
.inputRadio {
    margin: 25px;
}
</style>