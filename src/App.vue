<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event" />
     <alerta v-if="exibirAlerta" :tipo="alerta.tipo"> 
        <template v-slot:titulo>
          <h5>{{ alerta.titulo }}</h5>
        </template>
        <p>{{ alerta.descricao }}</p>
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
    exibirAlerta: false,
    alerta: {titulo:'', descricao: '', tipo: ''}
  }),
  mounted(){
    this.emitter.on('alerta', (a) => {
      this.alerta = a
      console.log(this.alerta)
      this.exibirAlerta = true
      setTimeout(() => this.exibirAlerta = false , 4000)
    })
  }
}
</script>

<style scoped>
</style>
