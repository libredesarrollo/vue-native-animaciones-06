<template>
  <view class="center">
    <animated:view
      class="estatica"
      :style="{
        height: growth,
        width: growth,
        borderRadius: growth,
      }"
    />
  </view>
</template>

<script>

import {Animated, Easing} from 'react-native'

export default {
  data() {
    return {
      growth: 0,
    };
  },
  methods: {
      crecerAnimacion: function(){
          /*.timing(this.growth, {
              toValue: 400,
              duration: 5000,
              easing: Easing.linear*/
          Animated.spring(this.growth,{
          toValue: 400,
          friction: 1
          }).start(() => {
              this.growth = new Animated.Value(10)
              //this.crecerAnimacion()
              this.decrecerAnimacion()
          })
      },
      decrecerAnimacion: function(){
          this.growth = new Animated.Value(400)
          Animated.timing(this.growth, {
              toValue: 10,
              duration: 5000,
              easing: Easing.linear
          }).start(() => {
              this.growth = new Animated.Value(0)
              this.crecerAnimacion()
          })
      }

  },
  created() {
      this.growth = new Animated.Value(0)
  },
  mounted() {
      this.crecerAnimacion()
  },
};
</script>

<style>
.estatica {
  background-color: red;
  align-self: center;
}
.container {
  justify-content: center;
  flex: 1;
}
</style>