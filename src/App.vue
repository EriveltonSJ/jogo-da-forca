<template>
  <div id="app">
    <h1>Jogo da forca</h1>

    <section v-if="tela === 'inicio'" class="inicio">
      <formulario
        title="Defina a palavra"
        button="Próximo"
        v-if="etapa === 'palavra'"
        :action="setPalavra"
      />
      <formulario
        title="Defina a dica"
        button="Iniciar Jogo :)"
        v-if="etapa === 'dica'"
        :action="setDica"
      />
    </section>

    <section v-if="tela === 'jogo'" class="jogo">
      <jogo
        :erros="erros"
        :palavra="palavra"
        :dica="dica"
        :verificarLetra="verificarLetra"
        :etapa="etapa"
        :letras="letras"
        :jogar="jogar"
        :jogarNovamente="jogarNovamente"
      />
    </section>
  </div>
</template>

<script>
import './css/global.css'
import Formulario from './components/Formulario.vue'
import Jogo from './components/Jogo.vue'

export default {
  name: 'App',
  components: { Formulario, Jogo },
  data() {
    return {
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
      erros: 0,
      letras: []
    }
  },
  methods: {
    setPalavra: function (palavra) {
      this.palavra = palavra
      this.etapa = 'dica'
    },
    setDica: function (dica) {
      this.dica = dica
      this.tela = 'jogo'
      this.etapa = 'jogo'
    },
    verificarLetra: function (letra) {
      return this.letras.find((item) => item.toLowerCase() === letra.toLowerCase())
    },
    jogar: function (letra) {
      // adiciona letra jogada
      this.letras.push(letra)

      // validar o erro
      this.verificarErros(letra)
    },
    verificarErros: function (letra) {
      // acerto
      if (this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0) {
        return this.verificarAcertos()
      }

      // erros
      this.erros++

      // enforcados
      if (this.erros === 6) {
        this.etapa = 'enforcado'
      }
    },
    verificarAcertos: function () {
      let letrasUnicas = [...new Set(this.palavra.split(''))]
      if (letrasUnicas.length === this.letras.length - this.erros) {
        this.etapa = 'ganhador'
      }
    },
    jogarNovamente: function () {
      this.tela = 'inicio'
      this.etapa = 'palavra'
      this.palavra = ''
      this.dica = ''
      this.erros = 0
      this.letras = []
    }
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
