<template>
  <div class="jogo">
    <Forca 
      :erros="erros"
    />
  </div>
</template>

<script>
import Forca from '@/components/Forca.vue'

export default {
  name: 'TheJogo',
  components:{
    Forca,
  },
  props:{
    erros: Number,
  }
}
</script>

<style scoped>

</style>