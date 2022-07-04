<template>
  <div>
    <div v-if="loading">
      <page-loading/>
    </div>
    <transition>
      <div v-if="api">
        <h2>{{api.nome}}</h2>
        <div class="videoAula">
          <iframe :src="`https://www.youtube.com/embed/${api.youtube}`" title="YouTube video player" frameborder="0" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";  
export default {
  name: 'aula',
  props:['aula'],
  mixins: [fetchData],
  created() {
    this.fetchhome(`/aula/${this.aula}`);
  },
  beforeRouteUpdate(to, from, next){
    this.fetchhome(`/aula/${to.params.aula}`),
    next();
  } 
}
</script>

<style>
.videoAula{
  position: relative;
  padding-bottom: 56.25%;
}
.videoAula iframe{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>