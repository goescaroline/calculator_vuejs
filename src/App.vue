<script setup>

import { reactive } from 'vue';

const estado = reactive({
  filtro: '',
  numeroX: '',
  numeroY: '',
})

const soma = () => {
  return parseFloat(estado.numeroX) + parseFloat(estado.numeroY);
}

const subtrai = () => {
  return estado.numeroX - estado.numeroY;
}

const multiplica = () => {
  return estado.numeroX * estado.numeroY;
}

const divide = () => {
  return estado.numeroX / estado.numeroY;
}

const aplicaRegra = () => {
    const { filtro } = estado;
    switch (filtro) {
      case 'soma':
        return soma();
      case 'subtrai':
        return subtrai();
      case 'multiplica':
        return multiplica();
      case 'divide':
        return divide();
      default:
        return 'Preencha os valores'
    }
  }
</script>

<template>
  <header>
    <h1>Calculadora</h1>
  </header>
  <main>
    
    <input type="Number" :required="numeroX" @keyup="evento => estado.numeroX = evento.target.value">
    <input type="Number" required @keyup="evento => estado.numeroY = evento.target.value">
    
    <select @change="evento => estado.filtro = evento.target.value">
      <option value="vazio">Escolha a operaçao:</option>
      <option value="soma">+</option>
      <option value="subtrai">-</option>
      <option value="multiplica">*</option>
      <option value="divide">/</option>
    </select>
    
    
  </main>
 <div>
  {{ aplicaRegra() }}
 </div>
</template>

<style scoped>

</style>
