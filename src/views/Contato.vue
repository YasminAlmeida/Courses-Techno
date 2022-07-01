<template>
  <div>
    <div v-if="loading">
      <page-loading/>
    </div>
    <transition>
      <div v-if='api'>
        <h1>Contato</h1>
        <p>{{api.descricao}}</p>
        <!-- <p>{{api}}</p> -->
        <ul>
          <li>
            <b>Email:</b>
            {{api.contato.email}}
          </li>
          <br>
          <li>
            <b>telefone:</b>
            {{api.contato.telefone}}
          </li>
          <br>
          <li>
            <b>endereco:</b>
            {{api.contato.endereco}}
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from '@/mixins/fetchData.js'
export default {
name:'contato',
mixins: [fetchData],
  created(){
    this.fetchhome("/contato");
  }
}
</script>

<style>

</style>