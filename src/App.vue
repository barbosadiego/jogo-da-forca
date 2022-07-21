<template>
  <div id="app">
    <div class="game-container">
      <h1>Jogo da Forca</h1>

      <section v-if="tela === 'inicio'" >
        <Formulario 
          v-if="etapa === 'palavra'"
          texto="Defina a Palavra"
          button="Próximo"
          :action="setPalavra"
        />
        <Formulario
          v-if="etapa === 'dica'"
          texto="Defina a Dica"
          button="Iniciar Jogo"
          :action='setDica'
        />
      </section>
      
      <section v-if="tela === 'jogo'" id="jogo">
        Jogo
      </section>

    </div>
  </div>
</template>

<script>
import Formulario from '@/components/Formulario.vue';

export default {
  name: 'App',
  data(){
    return{
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
    }
  },
  components: {
    Formulario,
  },
  methods: {
    setPalavra(palavra){
      this.palavra = palavra;
      this.etapa = 'dica';
    },
    setDica(dica){
      this.dica = dica;
      this.etapa = 'jogo';
      this.tela = 'jogo';
    }
  }
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
#jogo{
  text-align: center;
  color: var(--color-text-light);
}
</style>
