<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="logo" />
        </h1>
        <button class="button" @click="changeTheme">
            {{ buttonText }}
        </button>
    </header>
</template>

<script>

export default {
    name: 'SideBar',
    emits: ['changeTheme'],
    data() {
        return {
            darkMode: false,
        }
    },
    computed: {
        buttonText() {
            return this.darkMode ? "Desativar modo escuro" : "Ativar modo escuro";
        }
    },
    methods: {
        changeTheme() {
            this.$emit('changeTheme', !this.darkMode);
            this.darkMode = !this.darkMode;
        }
    }
}
</script>

<style>
header {
    padding: 1rem 5rem 1rem 5rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>