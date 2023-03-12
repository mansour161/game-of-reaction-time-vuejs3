<template>
    <div class="block" v-if="showclock" @click="stoptimer">
        click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showclock: false,
            timer: null,
            reactiontime: 0


        }
    },
    mounted() {
        // console.log('mounted')
        setTimeout(() => {
            this.showclock = true
            this.starttimer();
        }, this.delay);
    },
    methods: {
        starttimer() {
            this.timer = setInterval(() => {
                this.reactiontime += 10

            }, 10);
        },
        stoptimer() {
            clearInterval(this.timer)
            this.$emit('end',this.reactiontime)
        }

    },
    // updated() {

    //     console.log("component updated")

    // },
    // unmounted() {
    //     console.log('component unmounted')
    // }

}
</script>


<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>