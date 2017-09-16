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

        <div v-show="isLivro()" class="container__main__livro">


          <div class="field">
            <span class="field__label">ID:</span>
            <input ref="livroId" class="field__input" type="text" v-model="livro.id">
          </div>

          <div class="field">
            <span class="field__label">Nome:</span>
            <input class="field__input" type="text" v-model="livro.nome">
          </div>

          <div class="field">
            <span class="field__label">Ordem:</span>
            <input class="field__input" type="text" v-model="livro.ordem">
          </div>

          <div class="field">
            <span class="field__label">Sigla:</span>
            <input class="field__input" type="text" v-model="livro.sigla">
          </div>

          <div class="field">
            <span class="field__label">Testamento:</span>
            <input class="field__input" type="text" v-model="livro.testamento">
          </div>

          <div class="buttons">
            <button type="button" @click="limpar">Limpar</button>
            <button type="button" @click="salvar">Salvar</button>
          </div>

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
                  <button type="button" @click="removeItem(l.id)">
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
  export default {
    data: () => ({
      page: '',
      livro: {
        id: null,
        nome: null,
        ordem: null,
        sigla: null,
        testamento: null
      },
      livros: []
    }),
    methods: {
      removeItem(id) {
        this.livros = this.livros.filter(i => Number(i.id) !== Number(id))
      },
      limpar() {
        this.livro = new Object()

        this.livro.id = null
        this.livro.nome = null
        this.livro.ordem = null
        this.livro.sigla = null
        this.livro.testamento = null


        this.$refs.livroId.focus()
      },
      isHome() {
        return this.page === 'home'
      },
      isLivro() {
        return this.page === 'livro'
      },
      addOnList(livro) {
        this.livros.push(Object.assign(livro))
      },
      salvar() {
        this.addOnList(this.livro)
        this.limpar()
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
