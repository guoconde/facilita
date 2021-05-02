<template>
  <div>
    <p class="noPrint">
      <strong >
        01) A biblioteca de uma universidade deseja fazer um algoritmo que leia
        o nome do livro que será emprestado, o tipo de usuário (professor ou
        aluno), o algoritmo deve imprimir um recibo mostrando o nome do livro, o
        tipo de usuário por extenso e o total de dias de empréstimo.
        <br />
        02) Considerar que o professor tem 10 dias para devolver o livro e o
        aluno somente 3 dias
      </strong>
    </p>
    <form v-if="!submit">
      <div>
        <span>
          Título do Livro:
          <input
            type="text"
            v-model="titleBook"
            placeholder="Digite o nome do livro"
          />
        </span>
        <span>
          Usuário:
          <select v-model="user">
            <option v-for="user in users" :value="user.cod" :key="user.cod">
              {{ user.cod }} - {{ user.name }}
            </option>
          </select>
        </span>
        <button class="btn" @click.prevent="getSubmit">Emprestar</button>
      </div>
    </form>
    <div class="print" v-else>
      <h1>RECIBO DE EMPRÉSTIMO</h1>
      <div class="printSpan">
        <span>Título: {{ titleBook }}</span>
      </div>
      <div class="printSpan">
        <span>Usuário: {{ user }} - {{ getUser() }}</span>
      </div>
      <div class="printSpan">
        <span>Data: {{ getDay() }}</span>
      </div>
      <div class="printSpan">
        <span>Devolução: {{ getDevolution() }}</span>
      </div>
      <div class="printSpan">
        <span>Ass: </span>
      </div>
      <button class="btn" @click.prevent="getBack">Voltar</button>
      <button @click="toPrint" class="btn">Imprimir</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    getUser() {
      return this.user == 1 ? "Professor" : "Aluno";
    },

    toPrint() {
      window.print();
    },

    getDay() {
      const todaysDay = new Date().toLocaleDateString("pt-BR");
      return todaysDay;
    },

    getDevolution() {
      const date = new Date();
      const newdate = new Date();

      if (this.user == 1) {
        const devolutionDate = newdate.setDate(date.getDate() + 10);
        const devolution = new Date(devolutionDate).toLocaleDateString("pt-BR");
        return devolution;
      } else {
        const devolutionDate = newdate.setDate(date.getDate() + 3);
        const devolution = new Date(devolutionDate).toLocaleDateString("pt-BR");
        return devolution;
      }
    },

    getSubmit() {
      this.submit = true;
    },

    getBack() {
      this.submit = false;
    },

  },

  data() {
    return {
      titleBook: "",
      submit: false,
      user: 1,
      users: [
        { name: "Professor", cod: 1 },
        { name: "Aluno", cod: 2 },
      ],
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

.print {
  width: 300px;
  background: #fff;
  margin: 0px 10px;
  padding: 20px;
  border: 3px solid #000;
  border-radius: 5px;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.printSpan {
  margin: 20px;
  font-size: 1.5rem;
  display: flex;
}

@media print {
  .noPrint {
    display: none;
  }
  button {
      display: none;
  }
}

</style>