<script setup>
import { reactive } from 'vue';


  const estado = reactive({
    numero1: 0,
    numero2: 0,
    filtro: '',
  })

  let resultado = 0;

  const somaValores = () => {
    const { numero1, numero2 } = estado;
    resultado = Number(numero1) + Number(numero2);
  }

  const subtraiValores = () => {
    const { numero1, numero2 } = estado;
    resultado = Number(numero1) - Number(numero2);
  }

  const multiplicaValores = () => {
    const { numero1, numero2 } = estado;
    resultado = Number(numero1) * Number(numero2);
  }

  const divideValores = () => {
    const { numero1, numero2 } = estado;
    resultado = Number(numero1) / Number(numero2);
  }

  const operacao = () => {
    const { filtro } = estado;

    switch(filtro) {
      case 'adicao':
        return somaValores();
      case 'subtracao':
        return subtraiValores();
      case 'multiplicacao':
        return multiplicaValores();
      case 'divisao':
        return divideValores();
      default:        
    }
  }

</script>

<template>

  <div class="container">
    <div class="card">

      <div class="colorHead card-header">
        <h1>Calculadora</h1>
      </div>

      <div class="card-body">  

        <select @change="evento => estado.filtro = evento.target.value" class="form-select" aria-label="Default select example">
          <option selected>Selecione uma operação</option>
          <option value="adicao">Adição (+)</option>
          <option value="subtracao">Subtração (-)</option>
          <option value="multiplicacao">Multiplicação (*)</option>
          <option value="divisao">Divisão (/)</option>
        </select>

        <label for="numero1">Primeiro número</label>
        <input @keyup="evento => estado.numero1 = evento.target.value" id="numero1" class="mt-3 ms-3 rounded-3" type="number" required> <br />
        <label for="numero2">Segundo número:</label>
        <input @keyup="evento => estado.numero2 = evento.target.value" id="numero2" class="mt-3 ms-3 rounded-3" type="number" required> <br />

        <p class="mt-3">Resultado:</p>
        <span :class="operacao()"> {{ resultado }}</span>
      </div>
    </div>
  </div>  


</template>

<style scoped>
  .colorHead {
    background-color: #42b883;
  }

</style>
