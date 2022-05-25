<template>
  <!-- Uma outra maneira de alterarmos a cor é com o bind style, criamos um objeto com as propriedades e insermos ele na tag -->
  <div class="box has-text-weight-bold" :style="estilo">
    <!-- Definição do Slot: O que tiver dentro do componente vai ser renderizado aqui -->
    <!-- Precisamos adicionar o slot porque lá no componente App.vue estamos colocando informações dentro desse componente aqui. -->
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: 'Box',
  data() {
    return {
      // podemos escrever a chave de duas formas
      // 1ª: 'background-color'    -> com aspas simples
      // 2ª backgroundColor        -> com camelCase
      estilo: {
        'background-color': '#FAF0CA'
      }
    }
  }
})
</script>
