<template>
  <div id="app">
    <button class="noPrint">Problema 01</button>
    <div class="noPrint">
      <FirstProblem></FirstProblem>
    </div>
    <button class="noPrint">Problema 02</button>
    <div>
      <SecondProblem></SecondProblem>
    </div>
    <button class="noPrint">Problema 03</button>
    <div class="noPrint">
      <ThirdProblem></ThirdProblem>
    </div>
    <button class="noPrint">Problema 04</button>
    <div class="noPrint"></div>
  </div>
</template>

<script>
import FirstProblem from './components/FirstProblem'
import SecondProblem from './components/SecondProblem'
import ThirdProblem from './components/ThirdProblem'

export default {
  name: 'App',
  components: { FirstProblem, SecondProblem, ThirdProblem }
}

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
	color: #FFF;
	background-color: #2196F3;
}

@media print {
  .noPrint {
    display: none;
  }
}

</style>
