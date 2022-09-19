<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>

  <lista-vagas :vagas="vagas"></lista-vagas>

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
  import ListaVagas from '@/components/comuns/ListaVagas.vue'
  import Indicador from '@/components/comuns/Indicador.vue'
    export default{
        name:'Home',
        components:{
          PesquisarVaga,
          Indicador,
          ListaVagas
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
          activated(){
          this.vagas = JSON.parse(localStorage.getItem('vagas'))
        },
        mounted() {
          this.emitter.on('filtrarVagas', vaga =>{
            const vagas = JSON.parse(localStorage.getItem('vagas'))
            this.vagas = vagas.filter(reg =>  reg.titulo.toLowerCase().includes(vaga.titulo.toLowerCase()) ) // true ou false: O método filter cria um novo array com todos os elementos que passaram no teste implementado na função
           })
        }
    }
</script>
<style scoped>
</style>
