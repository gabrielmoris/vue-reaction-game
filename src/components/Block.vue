<template>
    <div class="block" v-if="showBlock">
        <img
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
        };
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
        }, this.delay);
    },
};
</script>

<style>
.block {
    width: 450px;
    border-radius: 20px;
    background: #ecd907;
    color: white;
    text-align: center;
    /* padding: 100px 0;
    margin: 40px auto; */
}
img {
    width: 400px;
}
</style>
