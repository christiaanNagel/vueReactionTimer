<template>
    <div>
        <p>Reaction time: {{ score }} ms</p>
        <p class="rank"> {{ rank }} </p>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = "Best in the west"
        }
        else if (this.score < 500) {
            this.rank = "Average joe"
        }
        else {
            this.rank = "You sure you're not a sloth"
        }
    }
}
</script>

<style scoped>
.rank {
    font-size: 1rem;
    font-weight: bold;
    color: black;
}
</style>