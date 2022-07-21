<template>
  <div class="forca">
    <img :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${erros}.svg`">
  </div>
</template>

<script>
export default {
  name:'TheForca',
  props:{
    erros: Number,
  }
}
</script>

<style scoped>
.forca img{
  width: 100px;
}
</style>