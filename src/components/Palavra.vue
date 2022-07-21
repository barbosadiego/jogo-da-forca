<template>
  <div class="palavra">
    <div class="letras">
      <div class="letra" v-for="(item, key) in palavra" :key="key">
        <p>{{ item }}</p>
      </div>
    </div>
    <p class="dica">Dica: {{ dica }}</p>
  </div>
</template>

<script>
export default {
  name: 'ThePalavra',
  props: {
    palavra: String,
    dica: String,
  },
};
</script>

<style>
.palavra {
  display: flex;
  align-items: center;
  flex-direction: column;
  text-transform: uppercase;
}
.letras {
  max-width: 70%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-bottom: 30px;
}
.letra {
  width: 30px;
  border-bottom: 1px solid var(--color-text-light);
}
</style>
