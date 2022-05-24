<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>

    <div class="column is-three-quarter">
      <FormHeader />
      <div class="list">
        <Task />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import FormHeader from './components/FormHeader.vue';
import Task from './components/Task.vue';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormHeader,
    Task
  }
});
</script>

<style>
</style>
