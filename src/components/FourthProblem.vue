<template>
  <div>
    <div>
      <p>
        <strong>
          Criar um algoritmo com um campo que possa receber apenas números e
          vírgulas, separe os valores e valide aqueles que são números válidos
          da sequência de Fibonacci e imprima os números de forma crescente,
          conforme o exemplo:
          <br />
          <br />
          CAMPO RECEBE: 1,13,55,21,5,83
          <br />
          IMPRIME: 1,5,13,21,55
        </strong>
      </p>
    </div>
    <button v-if="start" @click="getStart" class="btn">Iniciar</button>
    <form action="" v-else>
      <input type="text" v-model="messageFib" id="input1" name="number" />
      <button class="btn" @click.prevent="getAnswer">Enviar</button>
      <div>
        <span v-if='answer != ""'>Input Na Sequência Fibonacci: <strong>{{ answer }}</strong></span>
      </div>
    </form>
    <div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    getStart() {
      this.start = false;

      setImmediate(() => {
        this.getAnswer();
      });
    },

    getAnswer() {
      this.getMessage();
      this.seqFibo();
      this.getArrString();
    },

    getMessage() {
      const numberInput = document.querySelector("#input1");

      numberInput.addEventListener("keypress", function (e) {
        if (!checkChar(e)) {
          e.preventDefault();
        }
      });

      function checkChar(e) {
        const char = String.fromCharCode(e.keyCode);

        const pattern = "[0-9]";

        if (char.match(pattern) || char.match(",")) {
          return true;
        }
      }
    },

    getArrString() {
      const getArray = this.messageFib.split(",");

      getArray.sort((a, b) => a - b);

      const arrayFiboOn = [];

      for (let i = 0; i < getArray.length; i++) {
        for (let j = 0; j < this.arrFibo.length; j++) {
          if (getArray[i] == this.arrFibo[j]) {
            arrayFiboOn.push(getArray[i]);
          }
        }
      }

      const arrayToString = arrayFiboOn.join();

      this.answer = arrayToString;
    },

    seqFibo() {
      let lastNumber = 0;
      let currentNumber = 1;
      let nextNumber = 2;

      if (this.arrFibo == []) {
        for (let i = 0; i < 30; i++) {
          this.arrFibo.push(currentNumber);
          lastNumber = currentNumber + nextNumber;
          currentNumber = nextNumber;
          nextNumber = lastNumber;
        }
      } else {
        this.arrFibo = [];
        for (let i = 0; i < 30; i++) {
          this.arrFibo.push(currentNumber);
          lastNumber = currentNumber + nextNumber;
          currentNumber = nextNumber;
          nextNumber = lastNumber;
        }
      }
    },
  },

  data() {
    return {
      messageFib: "",
      arrFibo: [],
      answer: "",
      start: true,
    };
  },
};
</script>

<style>
</style>
