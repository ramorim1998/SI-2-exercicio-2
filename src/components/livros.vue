<template>
  <div class="container ">
    <h1>Livros</h1>
    <form class="form-group">
        <p>
          <label for="titulo">Titulo: </label>
          <input v-model="titulo" class="input" type="text" id="titulo" name="titulo" required>
        </p>
         <p>
          <label for="sinopse">Sinopse: </label>
          <input v-model="sinopse" class="input" type="text" id="sinopse" name="sinopse" required>
        </p>
         <p>
          <label for="nome">Nome do autor: </label>
          <input v-model="nome" class="input" type="text" id="nome" name="nome" required>
        </p>
         <p>
          <label for="editora">Editora: </label>
          <input v-model="editora" class="input" type="text" id="editora" name="editora" required>
        </p>
        <p>
          <label for="ano">Ano: </label>
          <input v-model="ano" class="input" type="text" id="ano" name="ano" required>
        </p>
         <p>
          <label for="paginas">Páginas: </label>
          <input v-model="paginas" class="input" type="text" id="paginas" name="paginas" required>
        </p>

        <button class="btn btn-success mr-4" v-on:click="addLivro" @click.prevent>Salvar</button>
        <button class="btn btn-secondary" v-on:click="deleteLivros" @click.prevent>Limpar</button>
        <br>
        <h3>Lista de livros</h3>
        <ol v-if="listaLivros.length>0">
          <li v-for="livro of listaLivros" :key="livro.nome">
            {{livro.titulo}}
          </li>
        </ol>
    </form>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      listaLivros:[],
      titulo:'',
      sinopse:'',
      nome:'',
      editora:'',
      ano:'',
      paginas:''
    }
  },
  components: {
   
    
  }, methods:{
      addLivro(){
        if(this.titulo.trim()==='' || this.nome.trim()==='' || this.sinopse.trim()==='' || this.editora.trim()===''
        || this.ano.trim()==='' || this.paginas.trim()===''){
          console.log('bbbb');
          
          return
        }
        var objetc = {nome : this.nome,
        titulo : this.titulo,
        sinopse: this.sinopse,
        editora: this.editora,
        ano: this.ano,
        paginas: this.paginas}
        this.listaLivros.push(objetc)
        console.log(this.listaLivros);
        
      },
      deleteLivros(){
        this.listaLivros = []
      }

  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
