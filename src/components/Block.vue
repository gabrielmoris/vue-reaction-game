<template>
    <div class="block" v-if="showBlock">
        <img
            @click="stopTimer"
            src="https://media0.giphy.com/media/1gSpe0DA87PZs3Jcwt/giphy.gif?cid=790b7611c073793c535fa72957ea83cfcb8474adb1ccc45f&rid=giphy.gif&ct=g"
            alt="west-shooting"
        />
    </div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            showBlock: false,
            top: 0,
            left: 0,
            time: null,
            reactionTime: 0,
        };
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.top = `${Math.random() * 900 * Math.random()}px`;
            this.left = `${Math.random() * 1400 * Math.random()}px`;
            this.startTimer();
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.time = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            clearInterval(this.time);
            this.$emit("end", this.reactionTime);
        },
    },
};
</script>

<style>
.block {
    width: 450px;
    height: 300px;
    border-radius: 20px;
    /* background: #ecd907; */
    color: white;
    text-align: center;

    position: absolute;
    top: v-bind(top);
    left: v-bind(left);
}
img {
    width: 400px;
    border-radius: 20px;
    cursor: url("../assets/cursor-gun.png"), auto;
}
</style>
