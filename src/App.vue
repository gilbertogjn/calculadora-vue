<script setup>
import { reactive } from 'vue';

const state = reactive({
  valorA: 0,
  valorB: 0,
  operador: '',
  resultado: ''
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
  <div id="container" class="container">
    <div class="row">
      <div class="col">
        <h1 class="">Calculadora Aritimética</h1>
        <p>
          Insira os números no campos e selecione o tipo de operação aritimética
        </p>
      </div>
    </div>
    <form>
      <div class="row mb-2">
        <div class="col">
          <input @change="e => state.valorA = e.target.value" class="form-control" type="number" placeholder="Valor A">
        </div>
      </div>
      <div class="row mb-2">
        <div class="col">
          <input @change="e => state.valorB = e.target.value" class="form-control" type="number" placeholder="Valor B">
        </div>
      </div>
      <div class="row">
        <div class="col">
          <select @change="e => state.operador = e.target.value" class="form-control">
            <option value="" disabled selected>Selecione uma operação</option>
            <option value="soma">Soma</option>
            <option value="subtracacao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
      <div class="row">
        <span class="resultado" v-show="state.resultado !== ''">
          <h4 class="m-0 text-center">
            Resultado = {{ parseInt(operacao(state.operador)) }}
          </h4>
        </span>
      </div>
    </form>
  </div>
</template>

<style>

* {
  box-sizing: border-box;
}

#container {
  background-color: #30336b;
  width: 340px;
  padding: 40px;
  margin-top: 26px;
  border-radius: 8px;
  color: #c7ecee;
}

.resultado h4 {
  padding-top: 16px;
  font-weight: 600;
}
</style>
