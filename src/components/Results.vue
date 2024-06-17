<template>
    <div>
        <h2>Your reaction time is {{reactionTime}}ms</h2>
        <h3>Your rank is {{giveRank()}}</h3>
    </div>
  
</template>

<script>
export default {
    props: ['reactionTime'],

    methods:{
        giveRank(){
            if(this.reactionTime < 200){
                return 'Ninja'
            }else if(this.reactionTime < 300){
                return 'Samurai'
            }else if(this.reactionTime < 400){
                return 'Warrior'
            }else{
                return 'Beginner'
            }
        }
    }
}
</script>

<style scoped>


h3{
    color: #0faf87;
}

</style>