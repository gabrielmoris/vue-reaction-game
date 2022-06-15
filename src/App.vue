<template>
    <h1>Wild West Clickout</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" />
</template>

<script>
import Block from "./components/Block.vue";
export default {
    name: "App",
    components: { Block },
    data() {
        return {
            isPlaying: false,
            delay: null,
        };
    },
    methods: {
        start() {
            this.delay = 3000 + Math.random() * 10000;
            this.isPlaying = true;
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
