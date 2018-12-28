<template>
  <div id="app">
  <banner :carouselList="list"/>
  </div>
</template>

<script>
import banner from './components/banner'

export default {
  name: 'App',
  data(){
    return {
      list:[
        {id:"1",img:"../../static/img/james_harden.jpg"},
        {id:"2",img:"../../static/img/james_harden-002.jpg"},
        {id:"3",img:"../../static/img/james_harden-010.jpg"},
      ],

    }
  },
  components: {
    banner
  }
}
</script>

<style>
</style>
