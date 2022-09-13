<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>

   <div class="row mt-5" v-for="(vaga,index) in vagas" :key="index">
    <div class="col">
      <vaga v-bind="vaga" />
    </div>
  </div>


  <div class="row mt-5">
    <div class="col-4">
      <indicador titulo="Vagas abertas" indicador="100" bg="bg-dark" color="text-white"></indicador>
    </div>

    <div class="col-4">
      <indicador titulo="Profissionais cadastrados" indicador="225" bg="bg-dark" color="text-white"></indicador>
    </div>

    <div class="col-4">
      <indicador titulo="Visitantes online" :indicador="usuarioOnline" bg="bg-light" color="text-dark"></indicador>
    </div>
  </div>
  </div>
</template>

<script>
  import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'
  import Indicador from '@/components/comuns/Indicador.vue'
  import Vaga from '@/components/comuns/Vaga.vue'
    export default{
        name:'Home',
        components:{
          PesquisarVaga,
          Indicador,
          Vaga
        },
        data: () => ({
          usuarioOnline : 0,
          vagas: []
        }),
        methods: {
          getUsuarioOnline(){
           this.usuarioOnline = Math.floor(Math.random() * 101)
          }
        },

        created(){
          setInterval(this.getUsuarioOnline, 1000)
        },

        //mounted(){
          activated(){
          this.vagas = JSON.parse(localStorage.getItem('vagas'))
        }
    }
</script>
<style scoped>
</style>
