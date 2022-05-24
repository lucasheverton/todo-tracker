<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">
        Descrição da tarefa.
      </div>
      <div class="column">
        <Timer :tempoEmSegundos="10" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Timer from "./Timer.vue";

export default defineComponent({
  name: 'Task',
  components: {
    Timer
  }
})
</script>
