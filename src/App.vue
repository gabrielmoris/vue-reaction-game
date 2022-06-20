<template>
    <h1>Wild West Clickout</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
    name: "App",
    components: { Block, Results },
    data() {
        return {
            isPlaying: false,
            delay: null,
            score: null,
            showResults: false,
        };
    },
    methods: {
        start() {
            this.delay = 3000 + Math.random() * 10000;
            this.isPlaying = true;
            this.showResults = false;
        },
        endGame(reactionTime) {
            this.score = reactionTime;
            this.isPlaying = false;
            this.showResults = true;
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
    color: #ffe100;
    width: 100vw;
    height: 100vh;
    background-image: url("./assets/wwbg.jpg");
    background-size: cover;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
}

* {
    margin: 0;
    box-sizing: border-box;
}

button,
button::after {
    width: 180px;
    height: 56px;
    font-size: 36px;
    font-family: "Bebas Neue", cursive;
    background: linear-gradient(45deg, transparent 5%, #ff013c 5%);
    border: 0;
    color: #fff;
    letter-spacing: 3px;
    /* line-height: 88px; */
    box-shadow: 6px 0px 0px #d9f600;
    outline: transparent;
    position: relative;
    cursor: url("./assets/cursor-gun.png"), auto;
}

button::after {
    --slice-0: inset(50% 50% 50% 50%);
    --slice-1: inset(80% -6px 0 0);
    --slice-2: inset(50% -6px 30% 0);
    --slice-3: inset(10% -6px 85% 0);
    --slice-4: inset(40% -6px 43% 0);
    --slice-5: inset(80% -6px 5% 0);

    content: "Shoot!";
    display: block;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(
        45deg,
        transparent 3%,
        #00e6f6 3%,
        #00e6f6 5%,
        #ff013c 5%
    );
    text-shadow: -3px -3px 0px #f8f005, 3px 3px 0px #00e6f6;
    clip-path: var(--slice-0);
}

button:hover::after {
    animation: 1s glitch;
    animation-timing-function: steps(2, end);
}

button:disabled,
button[disabled] {
    /* cursor: not-allowed; */
    cursor: auto;
    opacity: 0;
}

@keyframes glitch {
    0% {
        clip-path: var(--slice-1);
        transform: translate(-20px, -10px);
    }
    10% {
        clip-path: var(--slice-3);
        transform: translate(10px, 10px);
    }
    20% {
        clip-path: var(--slice-1);
        transform: translate(-10px, 10px);
    }
    30% {
        clip-path: var(--slice-3);
        transform: translate(0px, 5px);
    }
    40% {
        clip-path: var(--slice-2);
        transform: translate(-5px, 0px);
    }
    50% {
        clip-path: var(--slice-3);
        transform: translate(5px, 0px);
    }
    60% {
        clip-path: var(--slice-4);
        transform: translate(5px, 10px);
    }
    70% {
        clip-path: var(--slice-2);
        transform: translate(-10px, 10px);
    }
    80% {
        clip-path: var(--slice-5);
        transform: translate(20px, -10px);
    }
    90% {
        clip-path: var(--slice-1);
        transform: translate(-10px, 0px);
    }
    100% {
        clip-path: var(--slice-1);
        transform: translate(0);
    }
}
</style>
