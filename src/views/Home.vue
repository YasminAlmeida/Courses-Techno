<template>
  <div>
    <div v-if="loading">
     <page-loading/>
    </div>
    <transition>
      <div v-if='api' class="conteudo">
        <div>
          <h1>{{api.id}}</h1>
          <h2>Sobre: {{api.titulo}}</h2>
          <p>{{api.descricao}}</p>
          <router-link tag="button" class="btnCursos" to="/cursos">Cursos</router-link>
          <div class="avaliacoes">
            <h2>Avaliações</h2>
            <ul>
              <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
                <p>{{avaliacao.nome}}</p>
                <p>{{avaliacao.descricao}}</p>  
              </li>
            </ul>
          </div>
        </div>
        <img src="@/assets/learn.jpg" alt="Representação Estudo" srcset="">
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from '@/mixins/fetchData.js'
export default {
  name: 'home',
  mixins: [fetchData],
  created(){
    this.fetchhome("/home");
  }
};
</script>

<style scoped>
.btnCursos{
  background: #4b8;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 8px 10px;
  margin-top: 10px;
  font-size: 1.1rem;
  cursor: pointer;
  box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>