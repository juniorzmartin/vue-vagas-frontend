<template>
    <div class="row mt-5" v-for="(vaga,index) in vagas" :key="index">
        <div class="col">
            <vaga v-bind="vaga" />
        </div>
    </div>
</template>

<script>
import Vaga from '@/components/comuns/Vaga.vue'

export default ({
    name:'ListaVagas',
    components:{
        Vaga
    },
    data: () => ({
        vagas: []
    }),
    activated(){
         this.vagas = JSON.parse(localStorage.getItem('vagas'))
    },
    mounted() {
        this.emitter.on('filtrarVagas', vaga =>{
        const vagas = JSON.parse(localStorage.getItem('vagas'))
        this.vagas = vagas.filter(reg =>  reg.titulo.toLowerCase().includes(vaga.titulo.toLowerCase()) ) // true ou false: O método filter cria um novo array com todos os elementos que passaram no teste implementado na função
    })
    }
    
})
</script>
