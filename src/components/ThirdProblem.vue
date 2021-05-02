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
        <button class="btn" @click="newGrid">Gerar Matriz</button>
        <div v-if="choice == 'full'">
          <span> {{ grid }} </span>
        </div>
        <div v-else-if="choice == 'even'">
          <span> {{ gridEven }} </span>
        </div>
        <div v-else>
          <span> {{ gridOdd }} </span>
        </div>
      </div>
    </div>
    <div class="inputRadio">
      <span
        ><input type="radio" value="full" v-model="choice" /> Matriz
        Completa
      </span>
      <span
        ><input type="radio" value="even" v-model="choice" /> Matriz
        Par
      </span>
      <span
        ><input type="radio" value="odd" v-model="choice" /> Matriz
        Ímpar
      </span>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    setGrid() {
      if (this.arr1.length <= 4) {
        this.getArr1();
      } else if (this.arr1.length > 4 && this.arr2.length <= 4) {
        this.getArr2();
      } else if (this.arr2.length > 4 && this.arr3.length <= 4) {
        this.getArr3();
      } else if (this.arr3.length > 4 && this.arr4.length <= 4) {
        this.getArr4();
      } else if (this.arr4.length > 4 && this.arr5.length <= 4) {
        this.getArr5();
      }
    },
    getGrid() {
      this.grid.push(this.arr1);
      this.grid.push(this.arr2);
      this.grid.push(this.arr3);
      this.grid.push(this.arr4);
      this.grid.push(this.arr5);
    },
    getGridEven() {
      this.gridEven.push(this.arr1Even);
      this.gridEven.push(this.arr2Even);
      this.gridEven.push(this.arr3Even);
      this.gridEven.push(this.arr4Even);
      this.gridEven.push(this.arr5Even);
    },
    getGridOdd() {
      this.gridOdd.push(this.arr1Odd);
      this.gridOdd.push(this.arr2Odd);
      this.gridOdd.push(this.arr3Odd);
      this.gridOdd.push(this.arr4Odd);
      this.gridOdd.push(this.arr5Odd);
    },
    getRandom() {
      const min = 1;
      const max = 25;

      return Math.floor(Math.random() * (max - min + 1)) + min;
    },
    newGrid() {
      if (this.grid.length < 5) {
        this.getGrid();
        for (let i = 0; i < this.grid.length; i++) {
          this.setGrid();
        }
      } else {
        this.grid = [];
        this.arr1 = [];
        this.arr2 = [];
        this.arr3 = [];
        this.arr4 = [];
        this.arr5 = [];

        this.getGrid();
        for (let i = 0; i < this.grid.length; i++) {
          this.setGrid();
        }
      }
      this.evenOddNumbers();
    },
    evenOddNumbers() {
      if (this.gridEven == []) {
        this.getNumbers();
        this.getGridEven();
        this.getGridOdd();
      } else {
        this.gridEven = [];
        this.gridOdd = [];
        this.arr1Even = [];
        this.arr2Even = [];
        this.arr3Even = [];
        this.arr4Even = [];
        this.arr5Even = [];
        this.arr1Odd = [];
        this.arr2Odd = [];
        this.arr3Odd = [];
        this.arr4Odd = [];
        this.arr5Odd = [];
        this.getNumbers();
        this.getGridEven();
        this.getGridOdd();
      }
    },
    getNumbers() {
      for (let i = 0; i < this.arr1.length; i++) {
        if (this.arr1[i] % 2 == 0) {
          this.arr1Even.push(this.arr1[i]);
        } else {
          this.arr1Odd.push(this.arr1[i]);
        }
      }
      for (let i = 0; i < this.arr2.length; i++) {
        if (this.arr2[i] % 2 == 0) {
          this.arr2Even.push(this.arr2[i]);
        } else {
          this.arr2Odd.push(this.arr2[i]);
        }
      }
      for (let i = 0; i < this.arr3.length; i++) {
        if (this.arr3[i] % 2 == 0) {
          this.arr3Even.push(this.arr3[i]);
        } else {
          this.arr3Odd.push(this.arr3[i]);
        }
      }
      for (let i = 0; i < this.arr4.length; i++) {
        if (this.arr4[i] % 2 == 0) {
          this.arr4Even.push(this.arr4[i]);
        } else {
          this.arr4Odd.push(this.arr4[i]);
        }
      }
      for (let i = 0; i < this.arr5.length; i++) {
        if (this.arr5[i] % 2 == 0) {
          this.arr5Even.push(this.arr5[i]);
        } else {
          this.arr5Odd.push(this.arr5[i]);
        }
      }
    },
    getArr1() {
      for (let i = 0; this.arr1.length < 5; i++) {
        const random = this.getRandom();
        this.arr1.push(random);
      }
    },
    getArr2() {
      for (let i = 0; this.arr2.length < 5; i++) {
        const random = this.getRandom();
        if (this.arr2.length <= 4) {
          this.arr2.push(random);
        }
      }
    },
    getArr3() {
      for (let i = 0; this.arr3.length < 5; i++) {
        const random = this.getRandom();
        if (this.arr3.length <= 4) {
          this.arr3.push(random);
        }
      }
    },
    getArr4() {
      for (let i = 0; this.arr4.length < 5; i++) {
        const random = this.getRandom();
        if (this.arr4.length <= 4) {
          this.arr4.push(random);
        }
      }
    },
    getArr5() {
      for (let i = 0; this.arr5.length < 5; i++) {
        const random = this.getRandom();
        if (this.arr5.length <= 4) {
          this.arr5.push(random);
        }
      }
    },
  },
  data() {
    return {
      choice: 'full',
      grid: [],
      arr1: [],
      arr2: [],
      arr3: [],
      arr4: [],
      arr5: [],
      gridEven: [],
      gridOdd: [],
      arr1Even: [],
      arr2Even: [],
      arr3Even: [],
      arr4Even: [],
      arr5Even: [],
      arr1Odd: [],
      arr2Odd: [],
      arr3Odd: [],
      arr4Odd: [],
      arr5Odd: [],
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
  background-color: black;
}
.result {
  display: block;
}
.inputRadio {
    margin: 25px;
}
</style>