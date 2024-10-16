<script setup>
import { computed, reactive } from 'vue';

  const estado = reactive({
    num1: 0,
    num2: 0,
    operacao: 'adicao'
  })

  const resultado = computed(() => {
    const n1 = parseFloat(estado.num1);
    const n2 = parseFloat(estado.num2);

    switch (estado.operacao) {
      case 'adicao':
        return n1 + n2;
      case 'subtracao':
        return n1 - n2;
      case 'multiplicacao':
        return n1 * n2;
      case 'divisao':
        return n2 !== 0 ? n1 / n2 : 'Divisão por zero invalida!'
    }
  })

</script>

<template>
  <div class="container">
    <h1>Calculadora Aritmética</h1>

    <label for="num1">Número 1:</label>
    <input type="number" v-model="estado.num1" class="input-container">

    <label for="num2">Número 2:</label>
    <input type="number" v-model="estado.num2" class="input-container">

    <label for="operacao">Operação:</label>
    <select v-model="estado.operacao">
      <option value="adicao">+</option>
      <option value="subtracao">-</option>
      <option value="multiplicacao">*</option>
      <option value="divisao">/</option>
    </select>

    <h2 class="resultado">Resultado: {{ resultado }}</h2>
  </div>
</template>

<style scoped>
  :global(body) {
    background-color: black;
  }

  .container {
    font-family: Arial, sans-serif;
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    background-color: #f9f9f9;
  }

  h1 {
    text-align: center;
    color: #333;
  }

  .input-container {
    margin-bottom: 15px;
  }

  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }

  .resultado {
    text-align: center;
    font-size: 24px;
    color: #007bff;
    margin-top: 20px;
  }
</style>
