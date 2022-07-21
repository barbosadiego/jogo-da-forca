<template>
  <div id="app">
    <div class="game-container">
      <h1>Jogo da Forca</h1>

      <section v-if="tela === 'inicio'">
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
          :action="setDica"
        />
      </section>

      <section v-if="tela === 'jogo'" id="jogo">
        <Jogo
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
  </div>
</template>

<script>
import Formulario from '@/components/Formulario.vue';
import Jogo from '@/components/Jogo.vue';

export default {
  name: 'App',
  data() {
    return {
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
      erros: 0,
      letras: [],
    };
  },
  components: {
    Formulario,
    Jogo,
  },
  methods: {
    setPalavra(palavra) {
      this.palavra = palavra;
      this.etapa = 'dica';
    },
    setDica(dica) {
      this.dica = dica;
      this.etapa = 'jogo';
      this.tela = 'jogo';
    },
    verificarLetra(letra) {
      return this.letras.find(
        (item) => item.toLowerCase() === letra.toLowerCase(),
      );
    },
    jogar(letra) {
      this.letras.push(letra);
      this.verificarErros(letra);
    },
    verificarErros(letra) {
      if (this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0) {
        return this.verificarAcertos();
      }
      this.erros++;
      if (this.erros === 6) {
        this.etapa = 'enforcado';
      }
    },
    verificarAcertos() {
      let letrasUnicas = [...new Set(this.palavra.split(''))]
      if(letrasUnicas.length === (this.letras.length - this.erros)){
        this.etapa = 'ganhador'
      }
    },
    jogarNovamente(){
      this.palavra = '';
      this.dica = '';
      this.erros = 0;
      this.letras = [];
      this.tela = 'inicio';
      this.etapa = 'palavra';
    }
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
.game-container {
  display: grid;
  gap: 30px;
  text-align: center;
}
#jogo {
  text-align: center;
  color: var(--color-text-light);
}
button{
  background-color: var(--color-background-button);
  border: none;
  color: var(--color-text-light);
  padding: 15px 10px;
  font-size: 1rem;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
}
</style>
