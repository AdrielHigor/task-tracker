<template>
    <div class="box form">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="formulário para criação de tarefas">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="description" />
            </div>
            <div class="column">
                <FormTimer @on-timer-stopped="handleTimerStopped" />
            </div>
        </div>
    </div>
</template>

<script>
import FormTimer from './FormTimer.vue'

export default {
    name: 'FormTask',
    components: {
        FormTimer,
    },
    emits: ['saveTask'],
    data() {
        return {
            description: '',
        }
    },
    methods: {
        handleTimerStopped(timeRunning) {
            const task = {
                description: this.description,
                timeRunning: timeRunning,
            }

            this.$emit('saveTask', task)
            this.description = '';
        }
    }
}
</script>

<style>
.form {
    color: var(--primary-text);
    background-color: var(--primary-bg);
}
</style>