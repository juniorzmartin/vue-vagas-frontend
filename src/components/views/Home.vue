<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>
  <div class="row mt-5">
    <div class="col-4">
      <indicador></indicador>
    </div>

    <div class="col-4">
      <indicador></indicador>
    </div>

    <div class="col-4">
      <indicador></indicador>
    </div>
  </div>
  </div>
</template>

<script>
  import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'
  import Indicador from '@/components/comuns/Indicador.vue'
    export default{
        name:'Home',
        components:{
          PesquisarVaga,
          Indicador
        },
        created(){
          console.log("criado")
        },
        activated(){
          console.log("Componente ativado")
        },
        deactivated(){
          console.log("Componente desativado")
        },
        beforeUnmount(){
          console.log("Antes de desmontar/destruir")
        },
        unmounted(){
          console.log("Desmontado/destruido")
        },
    }
</script>
<style scoped>
</style>
