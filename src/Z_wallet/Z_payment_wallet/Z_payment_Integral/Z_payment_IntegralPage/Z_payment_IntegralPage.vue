<template>
<div>
    <div style="width: 3.75rem;height: 0.5rem;display: flex;justify-content: center;align-items: center;font-size: 0.16rem;border-bottom: 0.01rem solid gainsboro;">我的积分</div>
    <div>
        <div style="width: 3.75rem;height: 1.3rem;background-color: skyblue;font-size: 0.14rem;display: flex;justify-content: center;align-items: center;flex-wrap: wrap;">
            <div style="width: 3.75rem;display: flex;justify-content: center;font-size: 0.2rem;font-weight: 600">您目前柚分等级</div>
            <div style="width: 0.85rem;height: 0.85rem; border: 0.01rem solid yellow;border-radius: 0.8rem;text-align: center;line-height: 0.6rem;background-color: #d8c462">

                <div style="height:0.31rem;font-size: 0.3rem;text-align: center;color: #B8860B">{{member}}</div>
                <div style="height:0.21rem;font-size: 0.2rem;text-align: center;color: white" >{{integral}}</div>
            </div>

        </div>
        <div style="width: 3.75rem;display: flex;justify-content: center;flex-wrap: wrap">
            <div style="width: 3.65rem;height: 0.4rem; font-size: 0.16rem;display: flex; ">积分详情</div>
            <div style="width: 3.75rem;display: flex;justify-content: center;flex-wrap: wrap">

                <div style="width: 3.5rem;height:0.8rem;font-size: 0.14rem;border-bottom: 0.01rem solid gainsboro;" v-for="(getjf,jf) in getjfs" :key="jf">

                    <div style="width: 2rem;height:0.3rem;">充值金额：<span style="color: #63a35c">{{getjf.amount}}</span> <span>柚币</span></div>
                    <div style="width: 1.5rem;height:0.3rem;color: #03a9f4">获得积分：<span style="color: #ff9800">{{getjf.integral}}</span> <span>柚分</span></div>
                    <div style="font-size: 0.12rem；width:3.5rem;">充值时间 <span style="color: red;margin-left: 1.3rem">{{getjf.bill_time}}</span></div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
    export default {
        name: "Z_payment_IntegralPage",
        data() {
            return {
                member:'',
                integral:'',
                // inls:[],
                getjfs: []
            }
            // bill_time:'',
            // integral:'',
            // transType:0


        },
        methods: {
            postjf(){
                this.$axios.get('http://47.92.132.161:8000/youke/auth/?token=' + window.localStorage.getItem('token')).then(res => {
                    this.member = res.data.data.member
                    this.integral = res.data.data.integral
                    window.console.log(this.member)

                    window.console.log(res.data)

                })
            },
            getjf() {
                this.$axios.get('http://47.92.132.161:8000/youke/auth/bill/?token=' + window.localStorage.getItem('token')).then(res => {
                    this.getjfs = res.data.data.data
                    // window.console.log(this.getjfs)

                    // window.console.log(res.data)

                })
            },
        },
        mounted(){
            this. postjf()
            this.getjf()
        }
    }
</script>

<style scoped>

</style>
