<script setup>
  import { reactive } from 'vue';

  const state = reactive({
    valorA: 0,
    valorB: 0,
    operador: '',
    resultado: 0
  })

  function operacao(tipo) {
    switch (tipo) {
      case 'soma':
        return state.resultado = parseInt(state.valorA) + parseInt(state.valorB)
      case 'subtracacao':
        return state.resultado = state.valorA - state.valorB
      case 'multiplicacao':
        return state.resultado = state.valorA * state.valorB
      case 'divisao':
        return state.resultado = state.valorA / state.valorB
    }
  }
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h1>Calculadora Aritimética</h1>
        <p>
          Insira os números no campos e selecione o tipo de operação aritimética
        </p>
      </div>
    </div>
    <form>
      <div class="row">
        <div class="col">
          <input @change="e => state.valorA = e.target.value" class="form-control" type="number" placeholder="Valor A">
        </div>
        <div class="col">
          <input @change="e => state.valorB = e.target.value" class="form-control" type="number" placeholder="Valor B">
        </div>
        <div class="col">
          <select @change="e => state.operador = e.target.value" class="form-control">
            <option value="" disabled selected>Selecione uma operação</option>
            <option value="soma">Soma</option>
            <option value="subtracacao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
        <div class="col">
          <span class="resultado">
            Resultado = {{ parseInt(operacao(state.operador)) }}
          </span>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
