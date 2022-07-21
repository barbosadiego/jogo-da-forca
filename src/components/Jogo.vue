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
      v-if="etapa === 'jogo'"
      :letras="letras" 
      :verificarLetra="verificarLetra"
      :jogar="jogar"
    />

    <Final
      v-if="etapa != 'jogo' "
      :etapa="etapa"
      :texto="etapa === 'ganhador' ? 'Parabéns :)' : 'Tadinho :('"
      :jogarNovamente="jogarNovamente"
    />
  </div>
</template>

<script>
import Forca from '@/components/Forca.vue';
import Palavra from '@/components/Palavra.vue';
import Teclado from '@/components/Teclado.vue';
import Final from '@/components/FInal.vue'

export default {
  name: 'TheJogo',
  components: {
    Forca,
    Palavra,
    Teclado,
    Final,
  },
  props: {
    erros: Number,
    palavra: String,
    dica: String,
    verificarLetra: Function,
    etapa: String,
    letras: Array,
    jogar: Function,
    jogarNovamente: Function,
  },
};
</script>

<style scoped></style>
