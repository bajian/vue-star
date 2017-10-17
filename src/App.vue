<template>
  <div  id="app">
    <div class="test1">
        <star  @on-toggle="onToggle"  animate="animated rubberBand" color="#F05654" class="star-container">
        <i slot="icon" class="fa fa-heart"></i> 
      </star>
      <star  @on-toggle="onToggle" animate="animated zoomInUp" color="#F05654" class="star-container">
        <i slot="icon" class="fa fa-heart"></i> 
      </star>
      <star @on-toggle="onToggle" animate="animated slideInUp" color="#F05654" class="star-container">
        <i slot="icon" class="fa fa-heart"></i> 
      </star>
      <hr>
      注意：animate.css 需要在block 或者display:inline-block; 才有效
    </div>

    <div class="test2">
      <star :active="true" @on-toggle="onToggle"  animate="animated tada" color="#F05654" class="star-container">
        <i slot="icon" class="fa fa-bell fa-2x"></i> 
      </star>
      <star :active="true" @on-toggle="onToggle"  animate="animated rubberBand" color="rgb(125, 94, 63)" class="star-container">
        <i slot="icon" class="fa fa-heart fa-2x"></i> 
      </star>
      <star ref="mystar" :active="state" 
      @on-toggle="onToggle" 
      @on-animation-end="onAnimationEnd"  
      animate="animated rubberBand" class="star-container">
        <i slot="icon" class="fa fa-heart fa-2x"></i> 
      </star>
      <hr>
      <button @click="toggleIt">toggleTheThirdOne</button>
      <span>第三个使用了： 关联的state，会受其他star改变 </span>
    </div>


  </div>
</template>

<script>
import star from './components/vue-star'

export default {
  name: 'app',
  components: {
    star
  },
  data () {
    return {
      state: true,
    }
  },
    methods: {
    onToggle (state) {
      console.log('onToggle state=',state);
      this.state=state
    },
    onAnimationEnd () {
      console.log('onAnimationEnd');
    },
    toggleIt () {
      console.log('toggleIt');
      this.$refs['mystar'].toggle();
      //第二种修改的方式是直接修改active的值
    }
  },
}
</script>

<style>

.test1{
  font-size: 20px;
}

.star-container {
  color: #a9a9a9;
  margin-left: 20px;
}

.test1{
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button{
  cursor: pointer;
}



/*#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/



</style>
