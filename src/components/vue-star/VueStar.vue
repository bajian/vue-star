<template>
    <span class="VueStar__ground">
      <span class="VueStar__icon" @click="toggle" :class="AnimateClass" :style='{color:ColorValue}'>
        <slot name="icon"></slot>
      </span>
      <span @transitionend="_transitionend" class="VueStar__decoration" :class="[{ 'active':activeDecorationState},decorationClass]"></span>
    </span>
</template>

<script>
import { isColors } from './colorRE.js'
var firstLoad=true
export default {
  name: 'VueStar',
  props: {
    animate: String,
    color: {
      type: String,
      default: '#F05654'
      },
    active: {
      type: Boolean,
      default: false
      },
    decorationClass: {
      type: String,
      default: ''
    },
  },
  watch: {
    activeState: function (nowVal,preVal){
      if (!firstLoad)
      {
        this.activeDecorationState=nowVal
      }
        
      },
    active: function (nowVal,preVal){
      this.setState(nowVal)
      },
        },
  methods: {
    toggle () {
      this.activeState = !this.activeState
      this.$emit('on-toggle', this.activeState);
    },
    _transitionend () {
      this.activeDecorationState=false
      this.$emit('on-animation-end');
    },
    setState (state) {
      this.activeState = state
    }
  },
  data () {
    return {
      activeState: false,
      activeDecorationState: false,
    }
  },
  computed: {
    AnimateClass () {
      return this.activeState ? this.animate : ''
    },
    ColorValue () {
      return this.activeState ? this.color : ''
    }
  },
  mounted () {
    this.setState (this.active)
    setTimeout(()=>{
      firstLoad=false
    }, 50);
    if (this.color) {
      if (isColors(this.color)) {
        return
      } else {
        console.error('this color must be hexcolor or rgbcolor  --->vue-star',this.color)
      }
    } else {
      return
    }
  }
}
</script>

<style >
 @import './main.css';
</style>