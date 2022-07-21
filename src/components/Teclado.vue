<template>
  <div class="teclado">
    <button
      class="tecla"
      v-for="(letra, index) in 'abcdefghijklmnopqrstuvwxyz'"
      :key="index"
      :disabled="verificarLetra(letra)"
      @click="jogar(letra)"
    >
      {{ letra }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'TheTeclado',
  props: {
    letras: Array,
    verificarLetra: Function,
    jogar: Function,
  },
};
</script>

<style scoped>
.teclado {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 10px;
  max-width: 85%;
  margin: 30px auto;
}
.tecla {
  display: grid;
  place-items: center;
  width: 30px;
  height: 30px;
  background-color: var(--color-background-button);
  border-radius: 3px;
  cursor: pointer;
  border: none;
  color: var(--color-text-light);
  text-transform: uppercase;
  font-size: 1rem;
  font-weight: bold;
}
.tecla:disabled{
  opacity: .2;
}
</style>
