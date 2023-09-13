<template>
  <div class="forca">
    <img
      :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${erros}.svg`"
      alt=""
    />
  </div>
</template>

<script>
export default {
  name: 'Forca',
  props: {
    erros: Number
  },
  data() {
    return {}
  },
  methods: {}
}
</script>

<style scoped>
.forca img {
  max-width: 100px;
}
</style>
