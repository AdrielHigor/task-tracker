<template>
    <div class="is-flex is-align-center is-justify-content-space-between">
        <TimeCounter :time-running="timeRunning" />
        <button class="button" @click="startCounter" :disabled="counterRunning">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="stopCounter" :disabled="!counterRunning">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script>
import TimeCounter from './TimeCounter.vue';

export default {
    name: 'FormTimer',
    emits: ['onTimerStopped'],
    data() {
        return {
            timeRunning: 0,
            counter: 0,
            counterRunning: false,
        }
    },
    components: {
        TimeCounter,
    },
    methods: {
        startCounter() {
            // Começar a contagem
            this.counterRunning = true;

            this.counter = setInterval(() => {
                this.timeRunning += 1000;
            }, 1000);
        },
        stopCounter() {
            //Finalizar a contagem
            this.counterRunning = false;
            clearInterval(this.counter);

            this.$emit('onTimerStopped', this.timeRunning);

            this.timeRunning = 0;
        }
    }
}
</script>

<style scoped>

</style>