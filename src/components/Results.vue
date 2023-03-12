<template>
    <p>reaction time : {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
import { exportDefaultSpecifier } from '@babel/types';

export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        // if (this.score < 250) {
        //     this.rank = "perfect"
        // } else if (this.score < 600) {
        //     this.rank = "t was good, but try again"
        // } else {
        //     this.rank = "Who were you snail?"
        // }

        this.rank= this.score <250 ?
        this.rank = "that was perfect" : this.score <600 ? this.rank = "It was good, but try again" : this.rank = "Who were you snail?"
    }

}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: aqua;
    font-weight: bold;


}
</style>
