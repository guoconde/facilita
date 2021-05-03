<template>
  <div id="app">
    <h1>Gustavo Conde Ribeiro</h1>
    <h2>Teste prático para empresa Facilita</h2>
    <button class="noPrint" @click="openFirst">Problema 01</button>
    <div class="noPrint" v-if="problemOne">
      <FirstProblem></FirstProblem>
    </div>
    <br>
    <button class="noPrint" @click="openTwo">Problema 02</button>
    <div v-if="problemTwo">
      <SecondProblem></SecondProblem>
    </div>
    <br>
    <button class="noPrint" @click="openThree">Problema 03</button>
    <div class="noPrint" v-if="problemThree">
      <ThirdProblem></ThirdProblem>
    </div>
    <br>
    <button class="noPrint" @click="openFour">Problema 04</button>
    <div class="noPrint" v-if="problemFour">
      <FourthProblem></FourthProblem>
    </div>
  </div>
</template>

<script>
import FirstProblem from "./components/FirstProblem";
import SecondProblem from "./components/SecondProblem";
import ThirdProblem from "./components/ThirdProblem";
import FourthProblem from "./components/FourthProblem";

export default {
  name: "App",
  methods: {
    openFirst() {
      this.problemOne == false
        ? (this.problemOne = true)
        : (this.problemOne = false);
    },
    openTwo() {
      this.problemTwo == false
        ? (this.problemTwo = true)
        : (this.problemTwo = false);
    },
    openThree() {
      this.problemThree == false
        ? (this.problemThree = true)
        : (this.problemThree = false);
    },
    openFour() {
      this.problemFour == false
        ? (this.problemFour = true)
        : (this.problemFour = false);
    },
  },
  components: { FirstProblem, SecondProblem, ThirdProblem, FourthProblem },
  data() {
    return {
      problemOne: false,
      problemTwo: false,
      problemThree: false,
      problemFour: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  margin: 30px;
  padding: 10px 20px;
  font-size: 1.4rem;
  border-radius: 5px;
  color: #fff;
  background-color: grey;
}

@media print {
  .noPrint {
    display: none;
  }
}
</style>
