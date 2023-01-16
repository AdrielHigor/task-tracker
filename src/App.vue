<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode': darkMode }">
    <div class="column is-one-quarter">
      <SideBar @change-theme="handleChangeTheme" />
    </div>
    <div class="column is-three-quarter content">
      <FormTask @save-task="handleSaveTask" />
      <div class="lista">
        <Task v-for="(task, index) in tasks" :key="index" :time-running="task.timeRunning"
          :description="task.description" />

        <BoxContainer v-if="isEmptyTaskList">
          Nenhuma Tarefa Cadastrada Ainda
        </BoxContainer>
      </div>
    </div>
  </main>
</template>

<script>
import SideBar from './components/SideBar.vue';
import FormTask from './components/FormTask.vue';
import Task from './components/Task.vue';
import BoxContainer from './components/BoxContainer.vue';

export default {
  name: 'App',
  data() {
    return {
      tasks: [],
      darkMode: false,
    }
  },
  components: {
    SideBar,
    FormTask,
    Task,
    BoxContainer
  },
  computed: {
    isEmptyTaskList() {
      return this.tasks.length <= 0;
    }
  },
  methods: {
    handleSaveTask(task) {
      this.tasks.unshift(task)
    },
    handleChangeTheme(darkMode) {
      this.darkMode = darkMode;
    },
  }
}
</script>

<style>
.lista {
  padding: 1rem;
}

main {
  --primary-bg: #fff;
  --primary-text: #000
}

main.dark-mode {
  --primary-bg: #2b2d42;
  --primary-text: #ddd;
}

.content {
  background-color: var(--primary-bg);
}
</style>
