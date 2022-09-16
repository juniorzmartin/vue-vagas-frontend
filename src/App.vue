<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event" />
     <alerta v-if="exibirAlerta"> 
      <div class="alert alert-success" role="alert">
        <h5>Título do alerta</h5>
        <hr>
        <p>Descrição do alerta</p>
      </div>
     </alerta>

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
    componente: 'Home',
    exibirAlerta: false
  }),
  mounted(){
    this.emitter.on('alerta', () => {
      this.exibirAlerta = true
      setTimeout(() => this.exibirAlerta = false , 3500)
      console.log('Apresentar a mensagem de alerta customizada')
    })
  }
}
</script>

<style scoped>
</style>
