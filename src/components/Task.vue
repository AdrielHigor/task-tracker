<template>
    <BoxContainer>
        <div class="columns">
            <div class="column is-7">{{ description }}</div>
            <div class="column">
                <TimeCounter :time-running="timeRunning" />
            </div>
        </div>
    </BoxContainer>
</template>
<script>
import BoxContainer from './BoxContainer.vue';
import TimeCounter from './TimeCounter.vue';

export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Task',
    props: {
        description: {
            type: String,
            default: 'Descrição da Tarefa',
        },
        timeRunning: {
            type: Number,
            default: 0,
        }
    },
    components: {
        TimeCounter,
        BoxContainer
    }
}
</script>

<style>

</style>