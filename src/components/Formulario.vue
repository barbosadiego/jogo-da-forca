<template>
  <div class="formulario">
    <p>{{texto}}</p>
    <input type="text" v-model="inputValue">
    <button 
      @click="onSubmit('dica')" 
      :disabled="inputValue.length === 0">
      {{button}}
    </button>
  </div>
</template>

<script>
export default {
  name: 'TheFormulario',
  props:{
    texto: String,
    button: String,
    action: Function,
  },
  data(){
    return{
      inputValue: '',
    }
  },
  methods:{
    onSubmit(){
      this.action(this.inputValue);
      this.inputValue = '';
    }
  }
}
</script>

<style scoped>
.formulario{
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}
.formulario p{
  color: var(--color-text-light);
  font-size: 1.1rem;
}
.formulario input{
  padding: 15px 10px;
  border-radius: 5px;
  font-family: inherit;
  font-size: 1rem;
  text-align: center;
}
.formulario button{
  padding: 10px 15px;
  background-color: var(--color-background-button);
  border: none;
  border-radius: 5px;
  color: var(--color-text-light);
  font-size: 1rem;
  cursor: pointer;
}
.formulario button:hover{
  opacity: .8;
}
.formulario button:disabled{
  opacity: .2;
  pointer-events: none;
}
</style>