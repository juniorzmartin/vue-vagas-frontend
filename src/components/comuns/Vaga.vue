<template>
<div class="row mt-5">
    <div class="col">
      <div class="card">
        <div class="card-header bg-dark text-white">
          <div class="row">
            <div class="col d-flex justify-content-between">
              <div>
                {{titulo}}
              </div>
              <div>
                <div class="form-check form-switch">
                  <input class="form-check-input" type="checkbox" v-model="favoritada">
                  <label class="form-fheck-label">Favoritar</label>
                </div>
              </div>
            </div>
          </div>

        </div>
        <div class="card-body">
          <p>{{descricao}}</p>
        </div>
        <div class="card-footer">
          <small class="text-muted">Salário: R$ {{salario}} | Modalidade: {{getModalidade}} | Tipo: {{getTipo}} | Publicação: {{getPublicacao}}</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default ({
    name: 'Vaga',
    //props:['titulo','descricao','salario','modalidade','tipo','publicacao']
    data: () => ({
      favoritada: false,

    }),
    watch: {
      favoritada(valorNovo){
            let obj = {
            valtitulo : this.titulo,
            valmodalidade : this.getModalidade,
            valtipo : this.getTipo,
            valsalario:this.salario
          }
        if(valorNovo){
          this.emitter.emit('favoritarVaga',obj)
        }else {
          this.emitter.emit('desfavoritarVaga',obj)
        }
      }
    },
    props: {
        titulo: {
          type: String,
          required: true,
          validator(p){
            console.log('prop', p.length)
            if(p.length <6) return false
            return true
          }
        },
        descricao: {
          type:String,
          //default: 'O contratante não adicionou uma descrição para essa vaga'
          default() {
            return '*'.repeat(20)
          }
        },
        salario: {
          type: [String, Number],
          required: true
        },
        modalidade: {
          type: String,
          required: true
        },
        tipo: {
          type:String,
          required:true
        },
        publicacao: {
          type:String,
          required:true
        }
    },
        computed: {
          getModalidade(){
            switch(this.modalidade){
              case '1' : return 'Home Office'
              case '2' : return 'Presencial'
            }
            return ''
          },
          getTipo(){
            switch(this.tipo){
              case '1' : return 'CLT'
              case '2' : return 'PJ'
            }
            return ''
          },
          getPublicacao(){
            let dataPublicacao = new Date(this.publicacao)
            //return dataPublicacao.toLocaleString('pt-BR')
            return dataPublicacao.toLocaleDateString('pt-BR')
          }
        },methods: {
        }
})
</script>
