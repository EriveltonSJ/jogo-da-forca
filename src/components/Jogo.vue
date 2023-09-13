<template>
  <div class="jogo">
    <forca :erros="erros" />
    <palavra :palavra="palavra" :dica="dica" :verificarLetra="verificarLetra" :etapa="etapa" />
    <teclado
      v-if="etapa === 'jogo'"
      :letras="letras"
      :verificarLetra="verificarLetra"
      :jogar="jogar"
    />
    <final
      v-if="etapa != 'jogo'"
      :etapa="etapa"
      :texto="etapa === 'ganhador' ? 'Parabéns :)' : 'Perdeu :('"
      :jogarNovamente="jogarNovamente"
    />
  </div>
</template>

<script>
import Forca from './Forca.vue'
import Palavra from './Palavra.vue'
import Teclado from './Teclado.vue'
import Final from './Final.vue'

export default {
  name: 'Jogo',
  components: { Forca, Palavra, Teclado, Final },
  props: {
    erros: Number,
    palavra: String,
    dica: String,
    verificarLetra: Function,
    etapa: String,
    letras: Array,
    jogar: Function,
    jogarNovamente: Function
  },
  data() {
    return {}
  },
  methods: {}
}
</script>

<style scoped>
.jogo {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
</style>
