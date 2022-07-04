<template>
  <div>
    <div v-if="loading">
      <page-loading/>
    </div>
    <transition>
      <div v-if='api' class="conteudo">
        <div>
          <h1>Cursos</h1>
          <p>{{api.descricao}}</p>
        </div>
        <ul>
          <li class="curso" v-for="curso in api.cursos" :key="curso.id">
            <router-link :to="{name: 'curso', params:{curso: curso.id} }">{{curso.nome}} - {{curso.totalAulas}} aulas | {{curso.horas}} horas</router-link>
            <p>{{curso.descricao}}</p>  
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from '@/mixins/fetchData.js'
export default {
  name:'cursos',
  mixins: [fetchData],
  created(){
    this.fetchhome("/cursos");
  }
};
</script>

<style>
.curso a{
font-size: 1.4rem;
color: #000;
}
.curso{
  margin-bottom: 40px;
}
.curso li a:active{
  color: #4b8;
}
</style>