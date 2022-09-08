<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>
  </div>
</template>

<script>
  import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'

    export default{
        name:'Home',
        components:{
          PesquisarVaga
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
