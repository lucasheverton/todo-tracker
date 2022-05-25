<template>
  <header>
    <h1>
      <img src="@/assets/logo.png" alt="Alura Tracker" title="Alura Tracker">
    </h1>

    <button class="button" @click="alterarTema" v-text="textoDoBotao">
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent  } from "vue"
export default defineComponent ({
  name: 'SideBar',
  emits: ['aoTemaAlterado'],
  data() {
    return {
      darkMode: false
    }
  },
  computed: {
    textoDoBotao() {
     return this.darkMode ? 'Dark Mode Off' : 'Dark Mode On';
    }
  },
  methods: {
    alterarTema() {
      this.darkMode = !this.darkMode;
      this.$emit('aoTemaAlterado', this.darkMode);
    }
  }
})
</script>>

<style scoped>
header {
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  padding: 1rem;
  text-align: center;
  
}

@media screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
