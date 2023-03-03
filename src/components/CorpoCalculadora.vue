<script setup>
    const props = defineProps(['filtro', 'numero1', 'numero2', 'operacao', 'resultado'])
</script>

<template>
    <div class="card">
        <div class="colorHead card-header">
            <h1>Calculadora</h1>
        </div>
        <div class="card-body">  
            <select @change="props.filtro" class="form-select" aria-label="Default select example">
                <option selected>Selecione uma operação</option>
                <option value="adicao">Adição (+)</option>
                <option value="subtracao">Subtração (-)</option>
                <option value="multiplicacao">Multiplicação (*)</option>
                <option value="divisao">Divisão (/)</option>
            </select>
            <label for="numero1">Primeiro número</label>
            <input @keyup="props.numero1" id="numero1" class="mt-3 ms-3 rounded-3" type="number" required> <br />
            <label for="numero2">Segundo número:</label>
            <input @keyup="props.numero2" id="numero2" class="mt-3 ms-3 rounded-3" type="number" required> <br />
            <p class="mt-3">Resultado:</p>
            <span :class="props.operacao"> {{ props.resultado }}</span>
        </div>
    </div>
</template>

<style scoped>
  .colorHead {
    background-color: #42b883;
  }
</style>