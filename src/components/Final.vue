<template>
  <div class="final">
    <div :class="`final-texto ${etapa}`">{{ texto }}</div>
    <button class="final-btn" @click="jogarNovamente">Jogar novamente</button>
  </div>
</template>

<script>
export default {
  name: 'Final',
  props: {
    etapa: String,
    texto: String,
    jogarNovamente: Function
  }
}
</script>

<style scoped>
.final-texto {
  margin: 20px 0px;
  font-size: 26px;
  font-weight: bold;
}

.final-texto.enforcado {
  color: var(--color-text-error);
}
.final-texto.ganhador {
  color: var(--color-text-success);
}

.final-btn {
  font-size: 16px;
}
</style>
