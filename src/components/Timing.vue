<template>
  <section class="is-flex is-align-items-center is-justify-content-space-between">
    <!-- Passando a propriedade tempoEmSegundos para o componente filho -->
    <Timer :tempoEmSegundos="tempoEmSegundos" />
    <Button @clicado="iniciarContagem" :desabilitado="cronometroRodando" texto="play" icone="fa-play" />
    <Button @clicado="finalizarContagem" :desabilitado="!cronometroRodando" texto="stop" icone="fa-stop" />
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Timer from "./Timer.vue";
import Button from "./Button.vue";

export default defineComponent({
  name: 'Timing',
  emits: ['quandoTemporizadorFinalizado'],
  components: {
    Timer,
    Button
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false
    }
  },
  methods: {
    iniciarContagem() {
      this.cronometroRodando = true;
      // começar a contagem
      // 1s = 1000ms
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000)
    },
    finalizarContagem() {
      this.cronometroRodando = false;
      
      // para a contagem do setInverval
      clearInterval(this.cronometro)

      // o $emit recebe dois parâmetros.
      // o primeiro é o nome do evento
      // o segundo parâmetro é o dado em si que queremos passar.
      this.$emit('quandoTemporizadorFinalizado', this.tempoEmSegundos)

      this.tempoEmSegundos = 0;
    }
  }
})
</script>

<style>
</style>
