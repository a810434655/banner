<template>
 <div id="banenr">
   <img :src="imgSrc" :class="imgWidth==1 && imgHeight==1?'percentage':''" alt="">
   <ul class="ul" :style="ulAttrBute">
     <li v-for="(item,key) in carouselList" @mouseover="iconHover(key)" @mouseout="iconOut" @click="iconClick(key)" :style="{'background':date==key?act:col,'width':iconWidth+'px','height':iconWidth+'px','margin-left':between+'px'}" :key="key"></li>
   </ul>
 </div>

</template>

<script>
export default {
  name: 'banner',
  data () {
    return {
      //接受setintval的ID来结束他
       setIn:"",
      //所有轮播根据date来
       date:this.pop,
      //选中小圆点的颜色
       act:"",
      //默认小圆点的颜色
       col:"",
      //ul的宽
       ulWidth:"",
      //外侧div的宽度
       bannerWidth:"",
    }
  },
  computed:{
    imgSrc(){
      //、先执行computed如果this.date还没有值,那么默认为0
      if(this.date==false){
        return this.carouselList[this.date].img;
      }else{
        return this.carouselList[this.date].img;
      }
    },
    ulAttrBute(){
     return {'width':(this.iconWidth+this.between)*this.carouselList.length+'px','margin-left':(this.bannerWidth-((this.iconWidth+this.between)*this.carouselList.length))/2+'px'}
    }
  },
  mounted(){
    this.act=this.active;
    this.col=this.background;
    this.$nextTick(()=>{
      //获取包裹元素的DIV宽度
      this.bannerWidth=document.getElementById("banenr").offsetWidth;
      this.setInter();
    })
    
  },
  methods:{
    //按钮点击事件，点击后跳转相应图片
    iconClick(index){
      if(this.toggle=='click'){
        clearInterval(this.setIn);
        this.date=index;
      }else{
       return false;
      }
    },
    iconOut(){
      this.setInter();
    },
    iconHover(index){
      if(this.toggle=='hover'){
        clearInterval(this.setIn);
        this.date=index;
      }else{
        return false;
      }
    },
    // 是否自动轮播
    setInter(){
      this.setIn=setInterval(()=>{
        if(this.date==this.carouselList.length-1){
          this.date=0;
        }else{
          this.date++;
        }
      },this.interval);
    }
  },
  //轮播组件接收组件的宽度、高度、定时器间隔时间、轮播图List
  props:{
    // 切换方式
    toggle:{
      type:String,
      default:"hover"
    },
    //宽 默认为1的话是100%
    imgWidth:{
      type:Number,
      default:1
    },
    // 高 默认为1就会是100%
    imgHeight:{
      type:Number,
      default:1
    },
    //定时器时间
    interval:{
      type:Number,
      default:2000
    },
    //默认开始图片
    pop:{
      type:Number,
      default:0
    },
    //小圆点宽高
    iconWidth:{
      type:Number,
      default:15
    },
    //默认选中小圆点颜色
    active:{
      type:String,
      default:"#ffffff"
    },
    //默认小圆点颜色
    background:{
      type:String,
      default:"#03a9f4"
    },
    //小圆点间距
    between:{
      type:Number,
      default:5
    },
    //图片数据
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
    cursor: pointer;
  }

</style>
