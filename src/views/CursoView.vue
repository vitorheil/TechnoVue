<template>
    <div>
        <div v-if="loading">
            <PageLoading></PageLoading>
        </div>
        <transition>
  <div v-if="api" class="conteudo">
    <div>
    <h1>{{api.nome}}</h1>
    <p>{{api.descricao}}</p>
    <h2>Aulas</h2>
    <ul class="aulas">
        <li v-for="aula in api.aulas" :key="aula.id">{{aula.nome}}</li>
    </ul>
    </div>
  </div>
</transition>
</div>
</template>

<script>
import fetchData from "../mixins/fetchData.js"
import PageLoading from "@/components/PageLoading.vue";

export default {
    props: ["curso"],
    mixins: [fetchData],
    created() {
        this.fetchData(`/curso/${this.curso}`);
    },
    components: { PageLoading }
}
</script>

<style>
.aulas li {
    display: block;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, .1);
    background: white;
    padding: 20px;
    margin-bottom: 10px;
    border-radius: 4px;
}
</style>