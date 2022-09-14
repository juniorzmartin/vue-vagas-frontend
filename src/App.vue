<template>
  <div>
    <h1>Componente app</h1>
    <button @click="desmontarComponente()">Desmontar o componente conteudo</button>
    <topo-padrao :funcaoCallBack="acao" />
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
    acao(p1,p2){
      console.log("Função de callback definida no componente pai e chamada no componente filho")
      console.log('p1: ',p1,  ' p2:', p2)
    }
  }
}
</script>

<style scoped>
</style>
