<template>
  <button class="button" @click="clicado" :disabled="desabilitado">
    <span class="icon">
      <i class="fas" :class="icone"></i>
    </span>
    <span>{{ texto }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'Button',
  // emitimos um evento chamado 'clicado' para usarmos quando o componente for chamado no Timing.vue
  emits: ['clicado'],
  // props para fazer a comunicação com o elemento pai (Timing.vue)
  props: {
    desabilitado: {
      type: Boolean,
    },
    icone: {
      type: String,
      required: true
    },
    texto: {
      type: String,
      required: true
    }
  },
  methods: {
    clicado() : void {
      this.$emit('clicado');
    }
  }
})
</script>

<style>
</style>
