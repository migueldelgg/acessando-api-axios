<template>
  <div class="home">
    <h1>Bem vindo(a) estou aprendendo <span> {{tech}} </span>
    </h1>

    <NuxtLink to="/posts">Postagens</NuxtLink>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  data(){
    return{
      tech: 'Nuxt.js'
    }
  }
})
</script>

<style scoped>
h1{
  font-size: 2rem;
}
span{
  color: #4EC778;
}

</style>
