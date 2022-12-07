<template>
    <p class="results">Reaction time: {{ score }}  ms</p>
    <p class="rank">{{ rank }}</p>
</template>


<script>
export default {
    props: ["score"],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = "FAAAST FINGERS!!!"
        } else if (this.score < 400) {
            this.rank = "Rapid Reflexes!"
        } else {
            this.rank = "Snail Pace..."
        }
    }
}
</script>



<style>
    .results {
        font-size: 1.4em;
        font-weight: bold;
        color: #0faf87;
    }

    .rank {
        font-size: 1.8em;
        font-weight: bolder;
        color: darkmagenta;
    }
</style>