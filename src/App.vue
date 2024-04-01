<script setup>
import { reactive, ref } from "vue";

const titulo = ref('Título');

const mostrarResultado = ref(false)



const produto = reactive({
  nome: '',
  preco: 0,
  quantidade: 0,
  categorias: []

})

function formatarPreco(preco) {
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}
</script>

<template>
  <div class="container">
    <h1>{{ titulo }}</h1>
    <div class="formulario">
    <form @submit.prevent ="mostrarResultado = !mostrarResultado">

        <h2>Forms</h2>
        <input type="text" v-model="titulo" />
        <div class="row">
          <label for="">Nome:</label>
          <input type="text" v-model="produto.nome" required>
        </div>
        <div class="row">
          <label for="">Preço:</label>
          <input type="text" v-model="produto.preco">
        </div>
        <div class="row">
          <label for="">Quantidade:</label>
          <input type="number" v-model="produto.quantidade">
        </div>
        <div class="row">
          <label for="">Categorias:</label>
          <input type="text" v-model="produto.categorias">
        </div>
        <div class="mostrar">
          <button @submit ="mostrarResultado = !mostrarResultado">Mostrar</button>
        </div>
      </form>
      </div>

    
    <div class="resultado" v-if="mostrarResultado">
      <h2>Resultado</h2>
      <p>Nome: {{ produto.nome }}</p>
      <p>Preço: {{ formatarPreco(produto.preco *1) }}</p>
      <p>Quantidade: {{ produto.quantidade }}</p>
      <p>Categorias: {{ produto.categorias }}</p>
      <p>{{ mostrarResultado }}</p>
    </div>

  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 1.5rem;
  width: 100vw;
}

.formulario,
.resultado {
  width: 45%;
  border-radius: 10px;
  padding: 10px;
}

.formulario {
  background-color: #a8f0a2;
}

.resultado {
  background-color: #eeafe6;
}

.formulario .row {
  margin: 10px 20px;
  width: 80%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-align: center;
}

.mostrar {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: end;
}

.mostrar button {
  font-size: 17px;
  padding: 5px 10px;
  border-radius: 10px;
}
</style>