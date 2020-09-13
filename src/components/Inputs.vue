<template>
<div>
  <header>
    <img src="../img/img.png" alt="">
  </header>
    <label for="nome">Nome</label>
    <input class="form-control" type="text" v-model="nome" placeholder="Nome">
    <br>
    <label for="email">Email</label>
    <input class="form-control" type="email" v-model="email" placeholder="Email">
    <br>
    <label for="email">Nascimento</label>
    <input class="form-control" type="date" v-model="nascimento" placeholder="Email">

    <div class="form-group row mb-5 mt-5">
        <div class="col-sm-2">Services</div>
        <div class="col-sm-5">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" value="Processing - 1 micro - $ 1,00 per hour" id="1" v-model="checkbox" @click="check($event)">
            <label class="form-check-label" for="gridCheck1">Processing - 1 micro - $ 1,00 per hour</label> <br>
            <input class="form-check-input" type="checkbox" value="Processing - 1 medium - $ 2,00 per hour" id="2" v-model="checkbox" @click="check($event)">
            <label class="form-check-label" for="gridCheck2">Processing - 1 medium - $ 2,00 per hour</label><br>
            <input class="form-check-input" type="checkbox" value="Processing - 1 large - $ 10,00 per hour" id="3"  v-model="checkbox" @click="check($event)">
            <label class="form-check-label" for="gridCheck3">Processing - 1 large - $ 10,00 per hour</label><br>
          </div>
        </div>
        
        <div class="col-sm-5">
             <div class="form-check">
              <input class="form-check-input" type="checkbox" value="Storage - 10 GB HD - $ 0,5 per hour" id="4" v-model="checkbox" @click="check($event)">
              <label class="form-check-label" for="gridCheck1">Storage - 10 GB HD - $ 0,5 per hour</label> <br>
              <input class="form-check-input" type="checkbox" value="Storage - 1 TB HD - $ 1,00 per hour" id="5" v-model="checkbox" @click="check($event)">
              <label class="form-check-label" for="gridCheck1">Storage - 1 TB HD - $ 1,00 per hour</label><br>
              <input class="form-check-input" type="checkbox" value="Storage - 100 GB SSD - $ 5,00 per hour" id="6" v-model="checkbox" @click="check($event)">
              <label class="form-check-label" for="gridCheck1">Storage - 100 GB SSD - $ 5,00 per hour</label><br>
            </div>
        </div>
         
    </div>
    
    <div class="button">
        <button type="button" class="btn btn-primary btn-sm mb-5 mt-3 butao1" @click="adicionar()"  >Adicionar </button>
        <button type="button" class="btn btn-danger btn-sm mb-5 mt-3 butao2"  @click="apagar()" >Limpar Campos</button>
    </div>
    <span>Total de Registros {{total}} </span>                   

</div>
</template>

<script>
export default {
    name: 'Inputs',
    data() {
        return {
          
                nome: '',
                email:'',
                nascimento:'',
                checkbox: [],
                soma: 0,
                total:0
            
        }
    },

    methods: {
        check(e) {

            if (e.target.checked) {
                 if(e.target.id == 1){
                   this.soma += 1;
                 }
                 if(e.target.id == 2){
                   this.soma += 2;
                 }
                 if(e.target.id == 3){
                   this.soma += 10;
                 }
                 if(e.target.id == 4){
                   this.soma += 0.5;
                 }
                 if(e.target.id == 5){
                   this.soma += 1;
                 }
                 if(e.target.id == 6){
                   this.soma += 5;
                 }
             }
      },
      apagar(e){
                this.nome='';
                this.email='';
                this.nascimento= '';
                this.checkbox= [];
        },

        adicionar(){
            let dataNascimento = this.nascimento
            let dataCampo = new Date(dataNascimento)
            let dataAtual = new Date()
            let dia = dataAtual.getDate() - dataCampo.getDate()
            let mes = dataAtual.getMonth() - dataCampo.getMonth()
            let ano = dataAtual.getFullYear() - dataCampo.getFullYear()

            if(ano >= 18){
              let campos = {}
              campos.nome = this.nome
              campos.email = this.email
              campos.nascimento = this.nascimento
              campos.servicos = this.checkbox
              campos.total = this.soma
              this.tasks.push(campos)
  
              this.total++;

              localStorage.setItem('')

            }else{
              window.alert('[ERRO] Idade mínima = 18 anos')
            }
        },
    },
     mounted() {
      if(localStorage.nome){
        this.nome = localStorage.nome
      }

      if(localStorage.email){
        this.email = localStorage.email
      }

      if(localStorage.nascimento){
        this.nascimento = localStorage.nascimento
      }

      if(localStorage.total){
        this.total = localStorage.total
      }
    },

    watch: {
      nome(novoNome){
        localStorage.nome = novoNome
      },
      email(novoEmail){
        localStorage.nome = novoEmail
      },
      nascimento(novoNascimento){
        localStorage.nascimento = novoNascimento
      },
      total(novoTotal){
        localStorage.total = novoTotal
      }
    },
    
}
</script>

<style>
.butao1{
  margin-left: 450px;
}

.butao2{
  margin-left: 15px;
}
img{
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>