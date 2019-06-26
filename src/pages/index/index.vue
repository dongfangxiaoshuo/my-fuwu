<template>
  <div class="index">
    <div class="header">
      <p><van-icon name="location-o"/>{{position.district}}<span @click="toPosition">位置有误？点击更换</span></p>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      position:{}
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

<style scoped>
  .index{
    padding: 0 .3rem;
  }
  .header{
  }
  .header p{
    font-size:.3rem;
  }
  .header span{
    padding-left:.05rem; 
    font-size:.2rem;
  }
</style>
