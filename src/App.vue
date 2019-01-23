<template>
  <div id="app">
  <banner :carouselList="list" :pop="pos"  :interval="startmove"/>
  </div>
</template>

<script>
import banner from './components/banner'

export default {
  name: 'App',
  data(){
    return {
      pos:2,
      startmove:2000,
      list:[
        {img:"../../static/img/item1.jpg"},
        {img:"../../static/img/item2.jpg"},
        {img:"../../static/img/item3.jpg"},
      ],

    }
  },
  components: {
    banner
  }
}
</script>

<style scoped>
  #app{
    width: 50%;
    height: 50%;
  }
</style>
