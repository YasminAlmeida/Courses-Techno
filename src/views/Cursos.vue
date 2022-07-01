<template>
  <div>
    <div v-if="loading">
      <page-loading/>
    </div>
    <transition>
      <div v-if='api'>
        <h1>Cursos</h1>
        <p>{{api.descricao}}</p>
        <p>{{api}}</p>
        <!-- <ul>
          <li v-for="curso in api.cursos" :key="curso.id">
            <p>{{curso.name}}</p>
            <p>{{curso.totalAulas}}</p>  
          </li>
        </ul> -->
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

</style>