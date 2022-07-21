<template>
  <div class="jogo">
    <Forca :erros="erros" />

    <Palavra
      :palavra="palavra"
      :dica="dica"
      :verificarLetra="verificarLetra"
      :etapa="etapa"
    />

    <Teclado 
      :letras="letras" 
      :verificarLetra="verificarLetra"
      :jogar="jogar"
    />
  </div>
</template>

<script>
import Forca from '@/components/Forca.vue';
import Palavra from '@/components/Palavra.vue';
import Teclado from '@/components/Teclado.vue';

export default {
  name: 'TheJogo',
  components: {
    Forca,
    Palavra,
    Teclado,
  },
  props: {
    erros: Number,
    palavra: String,
    dica: String,
    verificarLetra: Function,
    etapa: String,
    letras: Array,
    jogar: Function,
  },
};
</script>

<style scoped></style>
