<template>
  <div class="palavra">
    <div class="palavra-letras">
      <div class="palavra-letra" v-for="(letra, key) in palavra" :key="key">
        {{ (verificarLetra(letra) || etapa === 'enforcado') ? letra : '' }}
      </div>
    </div>
    <div class="palavra-dica">
      {{ dica }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Palavra',
  components: {},
  props: {
    palavra: String,
    dica: String,
    verificarLetra: Function,
    etapa: String
  },
  data() {
    return {}
  },
  methods: {}
}
</script>

<style scoped>
.palavra {
  text-transform: uppercase;
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
}

.palavra-letras {
  display: flex;
  flex-direction: row;
  margin-bottom: 20px;
}

.palavra-letra {
  height: 30px;
  width: 30px;
  margin: 0 7px;
  border-bottom: 1px solid var(--color-text-light);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
