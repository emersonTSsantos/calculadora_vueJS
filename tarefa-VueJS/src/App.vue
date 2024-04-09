<template>
  <div class="container">
    <header>
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

      <h1>Calculadora VueJS</h1>
      <div class="wrapper">
        <input type="number" v-model.number="numero1" @input="calcular" placeholder="numero 1">
        <select v-model="operacao" @change="calcular">
          <option value="+">soma (+)</option>
          <option value="-">subtração (-)</option>
          <option value="*">multiplicação (*)</option>
          <option value="/">divizão (/)</option>
        </select>
        <input type="number" v-model.number="numero2" @input="calcular" placeholder="numero 2">
      </div>
    </header>

    <main>
      <div class="resultado">
        <p>Resultado: {{ resultado }}</p>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const numero1 = ref('');
const numero2 = ref('');
const operacao = ref('+');

const resultado = computed(() => {
  const n1 = parseFloat(numero1.value);
  const n2 = parseFloat(numero2.value);

  if (isNaN(n1) || isNaN(n2)) {
    return '---';
  }

  switch (operacao.value) {
    case '+':
      return n1 + n2;
    case '-':
      return n1 - n2;
    case '*':
      return n1 * n2;
    case '/':
      if (n2 !== 0) {
        return n1 / n2;
      } else {
        return 'Erro: divisão por zero';
      }
    default:
      return 0;
  }
});

</script>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .container {
    margin-left: 20%;
  }

  img {
    margin-left: 50%;
    width: 150px;
  }

  h1 {
    margin-left: 20%;
    font-size: 50px;
    color: rgb(97, 18, 18);
    text-align: center;
  }

  input {
    font-size: 60px;
  }

  select {
    margin-left: 40%;
    margin-top: 20px;
    margin-bottom: 20px;
    font-size: 20px;
  }

  .resultado {
    text-align: center;
    font-size: 40px;
  }
</style>
