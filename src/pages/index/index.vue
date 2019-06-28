<template>
  <div class="index">
    <div class="header">
      <p><van-icon name="location-o"/>{{position.district}}<span @click="toPosition">位置有误？点击更换</span></p>
    </div>

    <div class="main">
      <div class="title_wrap" >
        <div v-for="title in titles" v-bind:key="title.id">
          <img :src="title.image" alt="">
          <p>{{title.name}}</p>
        </div>
      </div>   

      <div class="extend_wrap">
        <div v-for="extend in extensions" v-bind:key="extend.id">
          <h5>{{extend.name}}</h5>
          <p>{{extend.info}}</p>
          <img :src="extend.image" alt="">
        </div>
      </div>

      
      

    </div>

  </div>
</template>

<script>
export default {
  data () {
    return {
      position:{},
      titles:[
        {
          id:1,
          name:"特惠洗车",
          image:"/static/images/1.png"
        },
        {
          id:2,
          name:"违章查询",
          image:"/static/images/2.png"
        },
        {
          id:3,
          name:"加油充值",
          image:"/static/images/3.png"
        },
        {
          id:4,
          name:"特价车险",
          image:"/static/images/4.png"
        },
        {
          id:5,
          name:"高价卖车",
          image:"/static/images/5.png"
        },
        {
          id:6,
          name:"4S店保养",
          image:"/static/images/6.png"
        },
        {
          id:7,
          name:"年检代办",
          image:"/static/images/7.png"
        },
        {
          id:8,
          name:"极速救援",
          image:"/static/images/8.png"
        },
        {
          id:9,
          name:"扫码移车",
          image:"/static/images/9.png"
        },
        {
          id:10,
          name:"全部服务",
          image:"/static/images/10.png"
        }
      ],
      extensions:[
        {
          id:1,
          name:"0元修车",
          info:"50元加油卷免费领",
          image:"/static/images/11.gif"
        },
        {
          id:2,
          name:"洗车不花钱",
          info:"众多好礼等你拿!",
          image:"/static/images/12.gif"
        },
        {
          id:3,
          name:"全国驾照",
          info:"限时免费领",
          image:"/static/images/13.gif"
        },
        {
          id:4,
          name:"骑士卡",
          info:"全球购物4折",
          image:"/static/images/14.gif"
        }
      ]
    }
  },
  methods: {
    toPosition(){

    }
  },

  created () {
    var that = this;
    wx.getLocation({type: 'wgs84',success (res) {
        console.log(res);
        wx.request({
          url: 'http://api.map.baidu.com/cloudrgc/v1?location='+res.latitude+','+res.longitude+'&geotable_id=135675&coord_type=bd09ll&ak=bdvtU9Cr8itfGWYUM8LzNKiQunv97wr3', //仅为示例，并非真实的接口地址
          header: {
            'content-type': 'application/json' // 默认值
          },
          success (res) {
            // console.log(res.data.address_component);
            that.position = res.data.address_component;
          }
        })
      }
    })
  }
}
</script>

<style scoped  lang=scss>

  .index{
    padding: 0 .3rem;
  }
  /* 头部区 */
  .header{
    padding-left:.2rem; 
    p{
      font-size:.3rem;
    }
    span{
      padding-left:.05rem; 
      font-size:.2rem;
    }
  }
  
  /* 主体曲 */
  .main{
  /* 主体标题区 */
    padding-top:.4rem; 
      .title_wrap{   
        font-size:.24rem;
        text-align: center;
        color:#858585;
        line-height: .4rem;   
        display: flex;
        justify-content: space-between;
        flex-wrap:wrap;
        div{
         padding: .2rem .2rem 0 .2rem;
        }
        img{
        height:.8rem;
        width: .8rem;
        }
      }
       /* 主体推广区 */
      .extend_wrap{
        margin-top:.3rem; 
        position: relative;
        h5{
          padding: .3rem 0 0 .2rem;
          font-size: .3rem;
         
        }
        p{
          line-height: .5rem;
          padding-left:.2rem; 
          color:#999;
          font-size:.25rem;
        }
        div{
          background: #f7f7f7;
          &:nth-child(1){
            position: absolute;
            top: 0;
            left:0;
            height: 4.3rem;
            width: 2.5rem;
            img{
              padding:.5rem; 
              width:1.5rem;
              height:1.5rem;
            }
          }
          &:nth-child(2){
            position: absolute;
            top: 0;
            right:0;
            height: 1.7rem;
            width: 4.2rem;
            img{
              position: absolute;
              right: 0.2rem;
              top: 0.35rem;
              width:1rem;
              height:1rem;
            }
          }
          &:nth-child(3){
            position: absolute;
            top: 1.8rem;
            left:2.65rem;
            height: 2.5rem;
            width: 2rem;
            border-left:#fff .1rem solid; 
            img{
              padding:.2rem .5rem 0 .5rem;             
              width:1rem;
              height:1rem;
            }
          }
          &:nth-child(4){
            position: absolute;
            top: 1.8rem;
            right:0;
            height: 2.5rem;
            width: 2rem;
            img{
              padding:.2rem .5rem 0 .5rem;             
              width:1rem;
              height:1rem;
            }
          }
        }
      }
  }
 

 
</style>
