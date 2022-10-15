<template>
    <div>
        <div class="block" v-if="showBlock" @click="stopTimer">
            Click me
        </div>
        <div v-else>
            ..Loading
        </div>
        <h6></h6>
    </div>
</template>

<script >
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
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        },
    }
}

</script>

<style  scoped>
.block {
    padding: 1rem;
    background-color: green;
    color: white;
    border-radius: 4px;
    width: 400px;
    margin: auto;
}
</style>