<template>
 <div id="banenr">
   <img :src="imgSrc" :class="width==1 && height==1?'percentage':''" alt="">
   <ul class="ul">
     <li v-for="(item,key) in carouselList" @click="iconOver(key)" :key="key" :style="{'background':pop==key?active+' !important':''}"></li>
   </ul>
 </div>

</template>

<script>
export default {
  name: 'banner',
  data () {
    return {

    }
  },
  computed:{
    imgSrc(){
      return this.carouselList[this.pop].img;
    },
  },
  mounted(){
    this.$nextTick(()=>{
      let banenrWidth=document.getElementById("banenr").offsetWidth;
      let ul=document.querySelector(".ul");
      let li=document.querySelectorAll(".ul>li");
      // 改变ul的宽高,让他可以适应居中
      for(var i=0;i<this.carouselList.length;i++){
        li[i].style.width=this.iconWidth+'px';
        li[i].style.height=this.iconWidth+'px';
        li[i].style.marginLeft=this.between+'px';
        li[i].style.background=this.color;
      }
      ul.style.width=(this.iconWidth+this.between)*this.carouselList.length+'px';
      ul.style.marginLeft=(banenrWidth-((this.iconWidth+this.between)*this.carouselList.length))/2+'px';
    })
  },
  methods:{
    iconOver(){

    }
  },
  //轮播组件接收组件的宽度、高度、定时器间隔时间、轮播图List
  props:{
    width:{
      type:Number,
      default:1
    },
    height:{
      type:Number,
      default:1
    },
    interval:{
      type:Number,
      default:2000
    },
    pop:{
      type:Number,
      default:2
    },
    iconWidth:{
      type:Number,
      default:15
    },
    active:{
      type:String,
      default:"#ffffff"
    },
    color:{
      type:String,
      default:"#03a9f4"
    },
    between:{
      type:Number,
      default:5
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
<style scoped>
  #banenr{
    width: 100%;
    height: 100%;
    position: relative;
  }
  a{
    display: block;
    width: 100%;
    height: 100%;
  }
  .ul{
    list-style: none;
    margin: 0 auto;
    position: absolute;
    bottom: 5%;
    padding: 0;
    margin: 0;
  }
 .percentage{
   width: 100%;
   height: 100%;
 }
  #banenr>img{
    display: block;
  }
  .ul>li{
    float: left;
    border-radius: 30px;
  }
  .active{
    background: red !important;
  }
</style>
