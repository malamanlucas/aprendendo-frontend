<template lang="html">
  <div class="livro">
    <h1>Meu componente de formulário</h1>

    <div class="field">
      <span class="field__label">ID:</span>
      <input ref="livroId" class="field__input" type="text" v-model="livro.id"
        :disabled="isEdit" />
    </div>

    <div class="field">
      <span class="field__label">Nome:</span>
      <input class="field__input" type="text" v-model="livro.nome" />
    </div>

    <div class="field">
      <span class="field__label">Ordem:</span>
      <input class="field__input" type="text" v-model="livro.ordem" />
    </div>

    <div class="field">
      <span class="field__label">Sigla:</span>
      <input class="field__input" type="text" v-model="livro.sigla" />
    </div>

    <div class="field">
      <span class="field__label">Testamento:</span>
      <input class="field__input" type="text" v-model="livro.testamento" />
    </div>

    <div class="buttons">
      <button type="button" @click="salvar">Salvar</button>
      <button type="button">Editar</button>
      <button type="button" @click="limpar">Limpar</button>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'formulario',
    data: () => ({
      livro: {
        id: null,
        nome: null,
        ordem: null,
        sigla: null,
        testamento: null
      },
      isEdit: false
    }),
    methods: {
      limpar() {
        this.livro = new Object()

        this.livro.id = null
        this.livro.nome = null
        this.livro.ordem = null
        this.livro.sigla = null
        this.livro.testamento = null

        this.$refs.livroId.focus()
        this.isEdit = false
      },
      salvar() {
        // this.$emit('click', this.livro)
        this.limpar()
      },
      editar() {
        this.$emit('on-edit-success', this.livro)
        this.limpar()
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import './formulario';
</style>
