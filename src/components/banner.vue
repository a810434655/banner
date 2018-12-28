<template>
 <div id="banenr">
   <a><img :src="carouselList[0].img" style="display: block" alt=""></a>
 </div>
  <ul>
    <li v-for="(item,key) in carouselList" :key="item.id"></li>
  </ul>
</template>

<script>
export default {
  name: 'banner',
  data () {
    return {
      pos:0,
      startmove:"",
    }
  },
  mounted(){
  },
  //轮播组件接收组件的宽度、高度、定时器间隔时间、轮播图List
  props:{
    width:{
      type:Number,
      default:900
    },
    height:{
      type:Number,
      default:400
    },
    interval:{
      type:Number,
      default:2000
    },
    carouselList:{
      type:Array,
      default:function () {
        return []
      }
    }
  }
}
</script>
<style>

</style>
