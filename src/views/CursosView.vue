<template>
  <div>
    <div v-if="loading">
      <PageLoading/>
    </div>
    <transition>
    <div v-if="api">
    <h1>{{api.titulo}}</h1>
    <p>{{api.descricao}}</p>
    <ul>
      <li v-for="curso in api.cursos" :key="curso.id">
        <h2>
          <router-link :to="{name: 'curso', params: {curso: curso.id}}">
          {{curso.nome}} - {{curso.totalAulas}} aulas | {{curso.horas}} horas
        </router-link>
        </h2>
        <p>{{curso.descricao}}</p>
      </li>
    </ul>
    </div>
  </transition>
  </div>
</template>

<script>
import fetchData from "../mixins/fetchData.js"
import PageLoading from "@/components/PageLoading.vue";

export default {
    mixins: [fetchData],
    created() {
        this.fetchData("/cursos");
    },
    components: { PageLoading }
}
</script>

<style>

</style>