<template>
    <div class="backr">
        <img @click="run" src="../../assets/L-img/back.png" >
        <p>注册</p>
    </div>
</template>

<script>
    export default {
        name: "Rheades",
        methods:{
            run(){
                this.$router.push({path:'/login'})
            },

        }
    }
</script>

<style scoped>
    .backr{
        display: flex;
        justify-content: space-between;
        margin-top: 0.1rem;
    }
    .backr img{
        width: 7%;
        height: 22px;
        margin-top: 2px;
    }
    .backr p{
        font-size: 0.2rem;
        width: 55%;
    }
</style>
