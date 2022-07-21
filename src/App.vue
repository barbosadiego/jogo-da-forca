<template>
  <div id="app">
    <div class="game-container">
      <h1>Jogo da Forca</h1>
      <Formulario />
      <Formulario />
    </div>
  </div>
</template>

<script>
import Formulario from '@/components/Formulario.vue';

export default {
  name: 'App',
  components: {
    Formulario,
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}
:root {
  --color-background: #2b343e;
  --color-background-button: #2980b9;
  --color-text-dark: #2c3e50;
  --color-text-light: #ecf0f1;
  --color-text-title: #1abc9c;
  --color-text-success: #2ecc71;
  --color-text-error: #c0392b;
}
body {
  background-color: var(--color-background);
  font-family: Arial, Helvetica, sans-serif;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
h1 {
  color: var(--color-text-title);
}
.game-container{
  display: grid;
  gap: 30px;
}
</style>
