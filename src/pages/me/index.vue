<template>
  <div class="me">

    <div class="header">
      <img src="/static/images/15.gif" alt="">
      <p>登陆/注册</p>
    </div>

    <div class="sort">
      <div><van-icon name="label-o" /><span>服务卷</span></div>
      <div><van-icon name="coupon-o" /><span>代金券</span></div>
      <div><van-icon name="cash-on-deliver" /><span>钱包</span></div>
    </div>

    <div class="fun">
      <van-cell title="白金会员" icon="vip-card-o" is-link />
      <van-cell title="消费记录" icon="cash-back-record" is-link />
      <van-cell title="我的爱车" icon="logistics" is-link />
      <van-cell title="我的银行卡" icon="idcard" is-link />
      <van-cell title="我的兑换码" icon="exchange" is-link />
      <van-cell title="邮寄地址" icon="free-postage" is-link />
      <van-cell title="分享" icon="cluster-o" is-link />

    </div>
    
  </div>
</template>

<script>


export default {
  data () {
    return {
     
    }
  },

  components: {
  
  },

  methods: {
   
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped lang=scss>
  .me{
    background: #f7f7f7;
    /* 头部 */
    .header{
      position: relative;
      height: 4rem;
      width: 100;
      background: #ff9000;
      img{
        border-radius: 50%;
        position: absolute;
        top:18%;
        left:38%;
        height: 2rem;
        width: 2rem;
      }
      p{
        position: absolute;
        top:68%;
        left:43%;
        color:#fff;
        font-size:.3rem;
      }
    }
    .sort{
      position: absolute;
      top:3.5rem;
      left:.25rem;
      padding: .2rem .5rem;
      display: flex;
      justify-content: space-between;
      border-radius:10px; 
      background: #fff;
      width: 80%;
      text-align: center;    
      div{     
        margin: 0 .5rem;
        display: flex;
        flex-direction:column; 
        span{
         color:#6b6b6b;
         font-size:.25rem;
        }
      }
    }
    .fun{
      padding-top:1rem;
      
    }
  }
</style>
