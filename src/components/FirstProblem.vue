<template>
  <div>
    <p>
      <strong>
        Chico tem 1,50 m e cresce 2 centímetros por ano, enquanto Juca tem 1,10
        m e cresce 3 centímetros por ano. Construa um algorítimo que calcule e
        imprima quantos anos serão necessários para que Juca seja maior que
        Chico.
      </strong>
    </p>
    <div class="column1">
      <span
        >Nome Pessoa 1
        <input type="text" v-model="personalData.name1" />
      </span>
      <span
        >Altura 1
        <input type="number" v-model="personalData.height1" />
      </span>
      <span
        >Taxa de Crescimento 1
        <input type="number" v-model="personalData.growthRate1" />
      </span>
    </div>
    <div class="column2">
      <span
        >Nome Pessoa 2
        <input type="text" v-model="personalData.name2" />
      </span>
      <span
        >Altura 2
        <input type="number" v-model="personalData.height2" />
      </span>
      <span
        >Taxa de Crescimento 2
        <input type="number" v-model="personalData.growthRate2" />
      </span>
    </div>
    <span class="answer" v-if="calcTime() != 0">{{ calcTime() }}</span>
  </div>
</template>

<script>
export default {
  methods: {
    calcTime() {
        
      const constName1 = this.personalData.name1;
      const constName2 = this.personalData.name2;
      const constHeight1 = this.personalData.height1;
      const constHeight2 = this.personalData.height2;
      const constGrowthRate1 = this.personalData.growthRate1;
      const constGrowthRate2 = this.personalData.growthRate2;

      if (constHeight1 > constHeight2 && constGrowthRate1 > constGrowthRate2) {
        return `${constName2} nunca será maior que ${constName1}`;
      } else if (
        constHeight1 < constHeight2 &&
        constGrowthRate1 < constGrowthRate2
      ) {
        return `${constName1} nunca será maior que ${constName2}`;
      } else {
        const result = Math.floor(this.calcHeight() / this.calcRate());
        return constHeight1 > constHeight2
          ? `${constName2} será maior que ${constName1} em ${result + 1} anos`
          : `${constName1} será maior que ${constName2} em ${result + 1} anos`;
      }
    },

    calcHeight() {
      let deltaHeight = "";
      if (this.personalData.height1 > this.personalData.height2) {
        deltaHeight += this.personalData.height1 - this.personalData.height2;
      } else {
        deltaHeight += this.personalData.height2 - this.personalData.height1;
      }
      return deltaHeight;
    },

    calcRate() {
      let deltaRate = "";
      if (this.personalData.growthRate1 > this.personalData.growthRate2) {
        deltaRate +=
          this.personalData.growthRate1 - this.personalData.growthRate2;
      } else {
        deltaRate +=
          this.personalData.growthRate2 - this.personalData.growthRate1;
      }
      return deltaRate;
    },
  },

  data() {
    return {
      personalData: {
        name1: "Chico",
        name2: "Juca",
        height1: 1.5,
        height2: 1.1,
        growthRate1: 0.02,
        growthRate2: 0.03,
      },
    };
  },
};
</script>

<style>
.column1 {
  display: flex;
  margin: 10px;
}
.column2 {
  display: flex;
  margin: 10px;
}
.answer {
  margin: 20px;
  font-size: 2rem;
}
</style>