<template>
  <div>
    <h1>Componente conteudo</h1>
    <p>Propriendade $style: {{$style}}</p>
    <div :class="$style['test-1']">Class test-1</div>
    <div :id="$style['test-2']">Class test-2</div>
    <home/>
    <publicar-vaga/>
  </div>
</template>

<script>
import Home from '../views/Home.vue'
import PublicarVaga from '../views/PublicarVaga.vue'

    export default{
        name:'Conteudo',
        components:{
          Home, 
          PublicarVaga
        }
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
