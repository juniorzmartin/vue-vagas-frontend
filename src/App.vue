<template>
  <div>
    <h1>Componente app</h1>
    <button @click="desmontarComponente()">Desmontar o componente conteudo</button>
    <topo-padrao @eventoCapturadoNoComponentePai="acao($event)" />
    <conteudo v-if="visibilidade" ></conteudo>
  </div>
</template>

<script>
import Conteudo from '@/components/layouts/Conteudo.vue'
import TopoPadrao from '@/components/layouts/TopoPadrao.vue'

export default {
  name: 'App',
  components: {
    Conteudo, 
    TopoPadrao
  },
  data: () => ({
    visibilidade: true
  }),
  methods: {
    desmontarComponente(){
      this.visibilidade = false
    },
    acao(e){
      console.log(e)
      console.log(e.msg)
    }
  }
}
</script>

<style scoped>
</style>
