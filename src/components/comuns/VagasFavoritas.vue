<template>
    <div>
        <div class="divVagasFavoritas">
            <button class="btn btn-primary" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight" aria-controls="offcanvasRight">Vagas Favoritas <span class="badge bg-secondary">{{vagas.length}}</span></button>
        </div>
        <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
            <div class="offcanvas-header">
                <h5 class="offcanvas-title" id="offcanvasRightLabel">Vagas Favoritadas </h5>
                <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
            </div>
            <div class="offcanvas-body">
                <ul class="list-group">
                    <li class="list-group-item" v-for="(vaga, index) in vagas" :key="index">
                        <p>Titulo: {{vaga.valtitulo}}, Modalide: {{vaga.valmodalidade}}, tipo: {{vaga.valtipo}}, salario: {{vaga.valsalario}}.</p>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:"VagasFavoritas",
    data: () => ({
        vagas: []
    }),
    mounted(){
        this.emitter.on('favoritarVaga',(obj) =>{
            this.vagas.push(obj)
        })

        this.emitter.on('desfavoritarVaga',(obj) =>{
             let indiceArray = this.vagas.findIndex(item => item.valtitulo === obj.valtitulo); //O método Array.findIndex permite encontrar o índice do elemento que satisfaz uma certa condição
             if(indiceArray !== -1) this.vagas.splice(indiceArray, 1) // splice remover um elemento à partir de um índice do array
        })      
    }
}
</script>

<style scoped>
    .divVagasFavoritas {
        position:absolute; z-index:1; top:70px; right:0px
    }
</style>