<template>
    <div class="results">
        <h2>You Lasted {{ score / 1000 }} seconds</h2>
        <h3>{{ rank }}</h3>
    </div>
</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            rank: null,
        };
    },
    mounted() {
        if (this.score < 350) {
            this.rank = "The fastest fingers in the West";
        } else if (this.score < 500) {
            this.rank = "Fast, but maybe not enough for the next time...";
        } else if (this.score < 700) {
            this.rank = "Did you shoot me...?? at least I wont die alone";
        } else {
            this.rank = "Go in peace, snail fingers";
        }
    },
};
</script>

<style>
.results {
    background-color: rgb(88, 88, 215);
    border-radius: 20px;
    box-shadow: 2px 2px #ff0000;
}
h2,
h3 {
    text-shadow: 2px 2px #ff0000;
    padding: 5px 10px;
}
</style>
