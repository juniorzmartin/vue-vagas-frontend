<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event" />
     <alerta v-if="exibirAlerta"> 

        <h3>Teste 1: Slot Padrão</h3>
        <template v-slot:titulo>
          <h5>Título Alerta</h5>
         </template>

         <div>
          <p><strong>Teste: Slot Padrão</strong></p>
         </div>

         <template v-slot:descricao>
          <p>Descrição do alerta</p>
         </template>

         <ul>
          <li>Teste 3: slot padrão</li>
          <li>Teste 3: slot padrão</li>
          <li>Teste 3: slot padrão</li>
         </ul>
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
