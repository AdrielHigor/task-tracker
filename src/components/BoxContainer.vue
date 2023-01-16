<template>
    <div class="box has-text-weight-bold">
        <slot></slot>
    </div>
</template>

<script>

export default {
    name: "BoxContainer"
}
</script>

<style scoped>
.box {
    background-color: #FAF0CA;
}
</style>