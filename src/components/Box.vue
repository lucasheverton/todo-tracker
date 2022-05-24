<template>
  <div class="box has-text-weight-bold">
    <!-- Definição do Slot -> O que tiver dentro do componente vai ser renderizado aqui -->
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'Box'
})
</script>
