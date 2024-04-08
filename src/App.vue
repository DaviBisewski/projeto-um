<script setup>
import { reactive, ref } from "vue";

const titulo = ref('Título');

const mostrarResultado = ref(false)



const pessoa = reactive({
  nome: '',
  email: '',
  senha: '',
  confsenha: '',
  estado: '',
  data: '',
  rua: 'Rua',
  numero: 'Número',
  bairro: 'Bairro',
  cidade: 'Cidade',
  cep: '00000-000',
})

function formatarPreco(preco) {
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}
</script>

<template>
  <div class="container">
    <h1>Formulário</h1>
    <div class="formulario">
      <form @submit.prevent="mostrarResultado = !mostrarResultado">
        <div class="row">
          <label for="">Nome:</label>
          <input type="text" v-model="pessoa.nome" required>
        </div>
        <div class="row">
          <label for="">Email:</label>
          <input type="email" v-model="pessoa.email">
        </div>
        <div class="row">
          <label for="">Senha:</label>
          <input type="password" v-model="pessoa.senha">
        </div>
        <div class="row">
          <label for="">Confirmar Senha:</label>
          <input type="password" v-model="pessoa.confsenha">
        </div>
        <div class="row">
          <label for="">Data de Nascimento:</label>
          <input type="date" v-model="pessoa.data">
        </div>
        <div class="row">
          <label for="">Endereço:</label>
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.rua">
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.numero">
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.bairro">
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.cidade">
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.cep">
        </div>
        <div class="row">
          <label for="">Estados:</label>
          <select v-model="pessoa.estado">
            <option value="AC">ACRE</option>
            <option value="AL">ALAGOAS</option>
            <option value="AP">AMAPÁ</option>
            <option value="AM">AMAZONAS</option>
            <option value="BA">BAHIA</option>
            <option value="CE">CEARÁ</option>
            <option value="DF">DISTRITO FEDERAL</option>
            <option value="ES">ESPÍRITO SANTO</option>
            <option value="GO">GOIÁS</option>
            <option value="MA">MARANHÃO</option>
            <option value="MT">MATO GROSSO</option>
            <option value="MS">MATO GROSSO DO SUL</option>
            <option value="MG">MINAS GERAIS</option>
            <option value="PA">PÁRA</option>
            <option value="PB">PARAÍBA</option>
            <option value="PR">PARANÁ</option>
            <option value="PB">PERNAMBUCO</option>
            <option value="PI">PIAUÍ</option>
            <option value="RJ">RIO DE JANEIRO</option>
            <option value="RN">RIO GRANDE DO NORTE</option>
            <option value="RS">RIO GRANDE DO SUS</option>
            <option value="RO">RONDÔNIA</option>
            <option value="RR">RORAIMA</option>
            <option value="SC">SANTA CATARINA</option>
            <option value="SP">SÃO PAULO</option>
            <option value="SE">SERGIPE</option>
            <option value="TO">TOCANTINS</option>
          </select>
        </div>

        <div class="row">
        <label for="">Linguagem de Programação</label>

        <div class="checkbox">
          <input type="checkbox" v-model="cmaismais" id="" />
          <p>C++</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" v-model="python" id="" />
          <p>Python</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" v-model="javascript" id="" />
          <p>JavaScript</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" v-model="java" id="" />
          <p>Java</p>
        </div>
        </div>
        <div class="row">
        <label for="">Hobbies favoritos</label>

        <div class="checkbox">
          <input type="checkbox" v-model="musica" id="" />
          <p>Musica</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" v-model="esportes" id="" />
          <p>Esportes</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" v-model="viagem" id="" />
          <p>Viagem</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" v-model="cozinhar" id="" />
          <p>Cozinhar</p>
        </div>
      </div>
      <div class="row">
        <label for="">Biografia:</label>
        <input type="text" v-model="biografia" id="" placeholder="Biografia:" />
    </div>


    <div class="mostrar">
      <button @submit="mostrarResultado = !mostrarResultado">Mostrar</button>
    </div>
    </form>
  </div>


  <div class="resultado" v-if="mostrarResultado">
    <h2>Resultado</h2>
    <p>Nome: {{ pessoa.nome }}</p>
    <p>Email: {{ pessoa.email }}</p>
    <p>Senha: {{ pessoa.senha }}</p>
    <p>Confirmar Senha: {{ pessoa.confsenha }}</p>
    <p>Data de Nascimento: {{ pessoa.data }}</p>
    <p>Rua: {{ pessoa.rua }}</p>
    <p>Número: {{ pessoa.numero * 1 }}</p>
    <p>Bairro: {{ pessoa.bairro }}</p>
    <p>CEP: {{ pessoa.cep * 1 }}</p>
    <p>Estado: {{ pessoa.estado }}</p>
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

.checkbox{
  display: flex;
}
</style>