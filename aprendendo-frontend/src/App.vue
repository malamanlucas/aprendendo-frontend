<template>
  <div id="app">

    <div class="container">

      <div class="container__nav">
        <span @click="goHome" class="brand">Home</span>
        <span v-bind:click="goLivro">Livro</span>
        <span>Livro Detalhe</span>
        <span @click="goCapitulo">Capitulo</span>
        <span>Versículo</span>
      </div>

      <div class="container__main">

        <div v-show="isHome()" class="container__main__home">
          <h1>home</h1>
        </div>

        <div v-show="isLivro()" class="container__main__livro">
          <h1>Livro</h1>
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
      page: ''
    }),
    methods: {
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
    }
  }
</script>

<style lang="scss" scoped>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    min-width: 100%;

    &__nav {
      border: 1px solid black;
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: center;
      font-size: 1.3em;
      span {
        &.brand {
          font-size: 1.5em;
        }
        cursor: pointer;
        &:hover {
          font-weight: bold;
          background: darken(white, 10%);
        }
      }
      flex-grow: 10;
    }

    &__main {
      border: 1px solid black;
      flex-grow: 80;
    }

    &__footer {
      border: 1px solid black;
      flex-grow: 10;
    }

  }


</style>
