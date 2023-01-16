<template>
    <section>
        <strong class="display">{{ parsedTimeRunning }}</strong>
    </section>
</template>

<script>
export default {
    name: 'TimeCounter',
    props: {
        timeRunning: {
            type: Number,
            default: 0,
        }
    },
    computed: {
        parsedTimeRunning() {
            return new Date(this.timeRunning).toISOString().substr(11, 8);
        },
    },
}
</script>

<style>
.display {
    color: var(--primary-text);
}
</style>