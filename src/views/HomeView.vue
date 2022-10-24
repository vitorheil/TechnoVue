<template>
  <div>
    <div v-if="loading">
      <PageLoading/>
    </div>
    <transition>
      <div v-if="api" class="conteudo">
        <div>
      <h1>Sobre a {{api.titulo}}</h1>
      <p>{{api.descricao}}</p>
      <router-link class="btnCurso" tag="button" to="/cursos">Cursos</router-link>
      <div>
        <h2>Avaliacoes</h2>
        <ul>
          <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
          <p>{{avaliacao.nome}}</p>
          <p>{{avaliacao.descricao}}</p>
        </li>
        </ul>
      </div>
      </div>
      <img src="../assets/aprender.png"/>
    </div> 
   </transition>
  </div>
</template>

<script>
import fetchData from "../mixins/fetchData.js"
import PageLoading from "../components/PageLoading.vue"

export default {
    name: "homeView",
    mixins: [fetchData],
    created() {
        this.fetchData("/home");
    },
    components: { PageLoading }
}
</script>

<style >
 .btnCurso{
    border: none;
    background: #3b8;
    border-radius: 3px;
    color: white;
    cursor: pointer;
    box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
    padding: 15px;
    font-size: 1rem;
    margin-bottom: 40px;
    font-family: 'Avenir';
 }
</style>