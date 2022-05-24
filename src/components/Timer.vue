<template>
  <strong>{{ tempoDecorrido }}</strong>
</template>

<script lang="ts">
import { defineComponent } from "vue"

export default defineComponent({
  name: 'Timer',
  //propriedades que vamos receber do componente pai (Timing.vue)
  props: {
    tempoEmSegundos: {
      type: Number,
      default: 0
    }
  },
  computed: {
    tempoDecorrido() : string {
      // pega o tempo * 1000 pra transformar em milisegundos
      // substr pega a partir da posição 11, 8 strings (apenas o horário)
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
    }
  }
})
</script>

<style>

</style>
