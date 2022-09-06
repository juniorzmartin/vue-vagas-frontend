<template>
  <div>
    <h1>{{titulo}}</h1>
    <button @click="atualizarComponente()">Atualizar</button>
    <button @click="conteudo='home'">Home</button>
    <button @click="conteudo='publicar-vaga'">Publicar Vaga</button>

    <!-- renderizar de forma dinamica os componentes home e publicas-vaga -->
    <!--<home/>-->
    <!--<publicar-vaga/> -->

    <keep-alive>
      <component :is="conteudo"/>
    </keep-alive>
  </div>
</template>

<script>
import Home from '@/components/views/Home.vue'
import PublicarVaga from '@/components/views/PublicarVaga.vue'

    export default{
        name:'Conteudo',
        components:{
          Home, 
          PublicarVaga
        },
        data: () =>({
          test: 'O componente foi criado',
          titulo: 'Componente conteudo',
          conteudo: 'home'

        }),
        methods:{
          atualizarComponente(){
            this.titulo += "*"
          }
        },
        /*
        beforeCreate() {
          console.log("Antes de criar", this.test)
        },
        created(){
          console.log("criado", this.test)
        },
        beforeMount(){
          console.log("Antes de montar o template, por exemplo, realizar uma requisição da API, trazendo do backend uma lista de informações para a montagem do template")
        },
        mounted(){
          console.log("Montado")
        },
        beforeUpdate(){
          console.log("Antes de atualizar")
        },
        updated(){
          console.log("Atualizado")
        },
        beforeUnmount(){
          console.log("Antes de desmontar/destruir")
        },
        unmounted(){
          console.log("Desmontado/destruido")
        },
        errorCaptured(){
          console.log("Erro capturado")
        },
        renderTracked(){
          console.log("Re-renderização rastreada")
        },
        renderTriggered(){
          console.log("Re-renderização acionada")
        },
        activated(){
          console.log("Componente ativado")
        },
        deactivated(){
          console.log("Componente desativado")
        }
        */
    }
</script>
<style module>
.test-1 {
  background-color: red;
}
#test-2{
  background-color: yellow;
}
</style>
