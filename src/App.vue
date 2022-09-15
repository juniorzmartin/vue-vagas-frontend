<template>
  <div>
    <alerta />
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event" />
    <conteudo v-if="visibilidade" :conteudo="componente"></conteudo>
  </div>
</template>

<script>
import Conteudo from '@/components/layouts/Conteudo.vue'
import TopoPadrao from '@/components/layouts/TopoPadrao.vue'
import VagasFavoritas from '@/components/comuns/VagasFavoritas.vue'
import Alerta from '@/components/comuns/Alerta.vue'

export default {
  name: 'App',
  components: {
    Alerta,
    Conteudo, 
    TopoPadrao, 
    VagasFavoritas
  },
  data: () => ({
    visibilidade: true,
    componente: 'Home'
  })
}
</script>

<style scoped>
</style>
