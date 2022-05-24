<template>
  <Box>
    <div class="columns">
      <div class="column is-7" v-text="tarefa.descricaoDaTarefa || 'Tarefa sem descrição'">
      </div>
      <div class="column">
        <Timer :tempoEmSegundos="tarefa.duracaoEmSegundos" />
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Timer from "./Timer.vue";
import vTask from "@/view/VTask";
import Box from "./Box.vue";

export default defineComponent({
  name: 'Task',
  components: {
    Timer,
    Box
  },
  props: {
    // recebendo a tarefa que está no v-for do componente pai (App.Vue)
    tarefa: {
      type: Object as PropType<vTask>,
      required: true
    }
  }
})
</script>
