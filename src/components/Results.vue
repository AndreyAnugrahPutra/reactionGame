<script>
export default {
    props: ['score'],
    data() 
    {
        return{
            rank: null,
            colorCode: null
        }
    },
    mounted()
    {
        if(this.score < 250)
        {
            this.rank = `Ninja Fingers!`
            this.colorCode = 'success'
        }
        else if(this.score < 400)
        {
            this.rank = `Good!`
            this.colorCode = 'primary'
        }
        else
        {
            this.rank = `Too Slow, LOL!`
            this.colorCode = 'danger'
        }
    }
    
}
</script>

<template>
    <div class="react-div">
        <h2 class="rank" :class="colorCode">{{ rank }}</h2>
        <h4>Your reaction time : {{ score  }}ms</h4>
    </div>
</template>

<style>
    .react-div, .rank
    {
        margin-top: 12px;
    }
    .success{color: #ffc107}
    .primary{color: #0d6efd}
    .danger{color: #dc3545}
</style>