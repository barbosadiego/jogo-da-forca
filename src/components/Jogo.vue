<template>
  <div class="jogo">
    <Forca 
      :erros="erros"
    />

    <Palavra 
      :palavra="palavra"
      :dica="dica"
    />
  </div>
</template>

<script>
import Forca from '@/components/Forca.vue'
import Palavra from '@/components/Palavra.vue'

export default {
  name: 'TheJogo',
  components:{
    Forca,
    Palavra,
  },
  props:{
    erros: Number,
    palavra: String,
    dica: String,
  }
}
</script>

<style scoped>

</style>