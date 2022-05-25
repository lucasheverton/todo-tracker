<template>
  <div class="box form">
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
  emits: ['aoSalvarTarefa'],
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
      this.$emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricaoDaTarefa: this.descricaoDaTarefa
      }        
        );
      this.descricaoDaTarefa = '';
    }
  }
})
</script>

<style>
  div.form {
    background: var(--bg--primary);
    color: var(--text-primary);
  }
</style>
