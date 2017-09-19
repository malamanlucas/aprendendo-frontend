<template>
  <div id="app">

    <div class="container">

      <div class="container__nav">
        <span @click="goHome" class="brand">Home</span>
        <span v-on:click="goLivro">Livro</span>
        <span>Livro Detalhe</span>
        <span>Capitulo</span>
        <span>Versículo</span>
      </div>

      <div class="container__main">

        <div v-show="isHome()" class="container__main__home">
          <h1>home</h1>
        </div>

        <div v-show="isLivro()">

          <formulario @click.native="alerta" />

          <table border="1">
            <thead>
              <tr>
                <th>#</th>
                <th>ID:</th>
                <th>NOME:</th>
                <th>ORDEM:</th>
                <th>SIGLA:</th>
                <th>TESTAMENTO:</th>
                <th>AÇÕES:</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(l, index) in this.livros">
                <td>{{ index+1 }}</td>
                <td>{{ l.id }}</td>
                <td>{{ l.nome }}</td>
                <td>{{ l.ordem }}</td>
                <td>{{ l.sigla }}</td>
                <td>{{ l.testamento }}</td>
                <td>
                  <button type="button" @click="comecarEdicao(l)">
                    Editar
                  </button>
                  <button type="button" @click="removeLivro(l.id)">
                    Remover
                  </button>
                </td>
              </tr>
            </tbody>
          </table>

        </div>

      </div>

      <div class="container__footer">
        footer
      </div>

    </div>

  </div>
</template>

<script>
  import Formulario from './components/Livro/Formulario'

  export default {
    components: {
      Formulario
    },
    data: () => ({
      page: '',
      livros: []
    }),
    methods: {
      alerta() {
        window.alert('qweq')
      },
      removeLivro(id) {
        this.livros = this.livros.filter(i => Number(i.id) !== Number(id))
      },
      comecarEdicao(livro) {
        this.isEdit = true
        this.livro = new Object()
        this.genericEdit(this.livro, livro)
      },
      genericEdit(destino, origem) {
        destino.id = origem.id
        destino.nome = origem.nome
        destino.ordem = origem.ordem
        destino.sigla = origem.sigla
        destino.testamento = origem.testamento
      },
      addOnList(livro) {
        this.livros.push(livro)
      },
      isHome() {
        return this.page === 'home'
      },
      isLivro() {
        return this.page === 'livro'
      },
      goHome() {
        this.page = 'home'
      },
      goLivro() {
        this.page = 'livro'
      }
    },
    mounted() {
      this.goLivro()
    }
  }
</script>

<style lang="scss" scoped>
  @import './app';
</style>
