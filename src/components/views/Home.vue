<template>
  <div>
    <h1>Componente Home</h1>
  </div>
</template>

<script>
    export default{
        name:'Home',
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
