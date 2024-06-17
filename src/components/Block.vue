<template>
    <div class="block" v-if="showBlock" @click="endTimer">
        click me
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
        console.log('Block mounted')
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
            console.log(this.delay);
        }, this.delay);
    },
    updated() {
        console.log('Block updated');
    },
    unmounted() {
        console.log('Block unmounted');
    },
    destroyed() {
        console.log('Block destroyed');
    },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },

        endTimer(){
            this.$emit('end', this.reactionTime);
            clearInterval(this.timer);
            console.log(this.reactionTime);
        }
    }

}
</script>

<style>
.block {
    width: 200px;
    height: 30px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px;
    margin: 50px auto;
    font-size: 30px;
}

</style>