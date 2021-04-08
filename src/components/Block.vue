<template>
    <div class="block" v-if='showBlock' @click='stopTimer'>
      How Fast Can You Click Me?!
    </div>
</template>

<script>
    export default {
        props: ['delay'],
        data() {
            return {
                showBlock: false,
                timer: null,
                reactionTime: 0
            }
        },
        mounted() {
            setTimeout(() => {
                this.showBlock = true
                this.startTimer()
            }, this.delay)
        },
        methods: {
            startTimer() {
                this.timer= setInterval(() => {
                    this.reactionTime += 10
                }, 10)
            },
            stopTimer() {
                clearInterval(this.timer)
                this.$emit('end', this.reactionTime)
            }
        }
    }
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #077056;
        color: #c9d1d9;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>