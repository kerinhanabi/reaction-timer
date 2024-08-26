<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
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
    //lets start the below 'mounted' function , a.k.a. in here is the timer, after this entire component is fully mounted on dom
    mounted() {
        // // can test this in browser inspect elements
        // console.log('component mounted')
        //starts timer for the block to show on screen
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            //console.log(this.delay)
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
            //console.log(this.reactionTime)
        }
    }
    // updated() {
    //     console.log('component updated')
    // },
    // unmounted() {
    //     //to test effect on inspect element , when in App.vue entire <Block /> has been removed or commented
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