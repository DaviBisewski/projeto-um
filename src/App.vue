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
  rua: '',
  numero: '',
  bairro: '',
  cidade: '',
  cep: '',
  linguas: '',
  hobbies: '',

})

function formatarPreco(preco) {
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}
</script>

<template>
  <div class="container">
    <div class="formulario">
      <form @submit.prevent="mostrarResultado = !mostrarResultado">
        <div class="title">
        <h1>Formulário</h1>
      </div>
        <div class="row">
           <input type="text" v-model="pessoa.nome" required placeholder="Nome:">
        </div>
        <div class="row">
            <input type="email" v-model="pessoa.email" placeholder="Email:">
        </div>
        <div class="row">
            <input type="password" v-model="pessoa.senha" placeholder="Senha:">
        </div>
        <div class="row">
          <input type="password" v-model="pessoa.confsenha" placeholder="Confirmar Senha:">
        </div>
        <div class="row">
          <input type="date" v-model="pessoa.data" placeholder="Data de Nascimento:">
        </div>
        <div class="row">
          <label for="">Endereço:</label>
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.rua" placeholder="Rua">
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.numero " placeholder="Número">
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.bairro" placeholder="Bairro">
        </div>
        <div class="row">
          <input type="text" v-model="pessoa.cidade" placeholder="Cidade">
        </div>
        <div class="row">
          <input type="number" v-model="pessoa.cep" placeholder="Cep">
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
          <div class="bglh">
        <div class="checkbox">
          <input type="checkbox" value="C++" id=""/>
          <p>C++</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" value="Python" id="" />
          <p>Python</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" value="JavaScript" id="" />
          <p>JavaScript</p>
        </div>
        <div class="checkbox">
          <input type="checkbox" value="Java" id="" />
          <p>Java</p>
        </div>
        </div>
      </div>
        <div class="row">
        <label for="">Hobbies favoritos</label>
        <div class="bglh">
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
    </div>
      <div class="row">
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
    <p>Hobbies: {{ pessoa.hobbies }}</p>
    <p>Linguagens: {{ pessoa.linguas }}</p>
  </div>

  </div>
</template>

<style scoped>
*{
  padding: 0;
  margin: 0;
  border: 0;
  box-sizing: border-box;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1.5rem;
  width: 100vw;
  height: 100vh;
  background-image: linear-gradient(to left, #1e2124, #282b30, #424549, #424549);

}

.formulario,
.resultado {
  padding: 20px;
  display: flex;
  flex-direction: column;
}

.formulario {
  background-color: #1e2124;
  justify-content: center;
  align-items: center;
}

h1{
  color: #fff;
}
.resultado {
  background-color: #7289da;
  width: 718px;
  justify-content: center;
  align-items: start;
  animation: spin 2s ease;
  animation-iteration-count: 1;
  gap: 10px;
}

.formulario .row {
  margin: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-align: center;
}

.formulario .row input{
  padding: 10px;
  border-radius: 0;
  border: 2px solid transparent;
  width: 100%;
}

.formulario .row input:hover{
  padding: 10px;
  border-radius: 0;
  border: 2px solid #7289da;
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

}

.checkbox{
  display: flex;
  align-items: center;
  justify-content: space-around;
  width: 100px;
}

.bglh{
  display: flex;
}

label{
  font-size: 1.5rem;
  color: #fff;
}

select{
  padding: 10px;
  color: #fff;
}

.title{
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
p{
  color: #fff;
}

@keyframes spin{
  to{
    transform: scale(1) translate(0px) rotate(0deg) translateY(0);
  }
  from{
    transform: scale(250) translate(2000px) rotate(720deg) translateY(1100px);
  }
}

.resultado p{
  font-size: 16px;
}
</style>