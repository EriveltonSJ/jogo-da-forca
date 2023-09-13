<template>
  <div class="formulario">
    <div class="formulario-title">{{ title }}</div>
    <input type="text" class="formulario-input" v-model="inputValue" />
    <button @click="onSubmit" :disabled="inputValue.length === 0">{{ button }}</button>
  </div>
</template>

<script>
export default {
  name: 'Formulario',
  props: {
    title: String,
    button: String,
    action: Function
  },
  data() {
    return {
      inputValue: ''
    }
  },
  methods: {
    onSubmit: function () {
      this.action(this.inputValue)
      this.inputValue = ''
    }
  }
}
</script>

<style scoped>
.formulario {
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

.formulario input {
  padding: 10px 5px;
  border: none;
  border-radius: 5px;
  margin: 20px 0px;
  text-align: center;
  color: var(--color-text-dark);
  font-size: 16px;
}
</style>
