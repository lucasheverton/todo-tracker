<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input class="input" placeholder="Qual tarefa você deseja iniciar?" type="text" v-model="descricaoDaTarefa">
      </div>

      <div class="column">
        <!-- Dentro do componente Timing vamos ouvir o evento personalizado (evento do emit que criei lá.) -->
          <Timing @quandoTemporizadorFinalizado="finalizarTarefa" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Timing from './Timing.vue'

export default defineComponent({
  name: 'FormHeader',
  components: {
    Timing
  },
  data() {
    return {
      descricaoDaTarefa: ''
    }
  },
  methods: {
    // criamos a função finalizar tarefa pegando como parâmentro o tempo decorrido 
    // que lá no $emit do componente Timing.vue passamos o segundo parâmetro tempoEmSegundos
    // que é o que vamos resgatar nessa função.
    finalizarTarefa(tempoDecorrido: number) : void {
      console.log("Tempo da tarefa --->", tempoDecorrido)
      console.log("Descrição --->", this.descricaoDaTarefa)
      this.descricaoDaTarefa = '';
    }
  }
})
</script>
