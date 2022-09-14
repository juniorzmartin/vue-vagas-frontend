<template>
  <div>
    <topo-padrao @navegar="componente = $event" />
    <conteudo v-if="visibilidade" :conteudo="componente"></conteudo>
  </div>
</template>

<script>
import Conteudo from '@/components/layouts/Conteudo.vue'
import TopoPadrao from '@/components/layouts/TopoPadrao.vue'

export default {
  name: 'App',
  components: {
    Conteudo, 
    TopoPadrao,
  },
  data: () => ({
    visibilidade: true,
    componente: 'Home'
  })
}
</script>

<style scoped>
</style>
