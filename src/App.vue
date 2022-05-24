<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>

    <div class="column is-three-quarter">
      <FormHeader @aoSalvarTarefa="salvarTarefa" />
      <div class="list">
        <!-- Vamos passa a prop "tarefa" para o componente filho com as informações de descricao e tempo em segundos -->
        <Task v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />

        <Box v-if="listaVazia">
          Você não está muito produtivo hoje :(
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import FormHeader from './components/FormHeader.vue';
import Task from './components/Task.vue';
import VTask from './view/VTask';
import Box from './components/Box.vue';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormHeader,
    Task,
    Box
  },
  data() {
    return {
      tarefas: [] as VTask[]
    }
  },
  methods: {
    salvarTarefa(tarefa: VTask) {
      this.tarefas.push(tarefa);
    }
  },
  computed: {
    listaVazia() : boolean {
      return this.tarefas.length === 0;
    }
  }
});
</script>

<style>
  .list {
    margin: 1em;
  }

  .list div {
    background: #ffe6c6;
  }
</style>
