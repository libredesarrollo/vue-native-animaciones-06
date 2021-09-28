<template>
  <view class="center">
    <animated:view
      class="estatica"
      :style="{
        height: 200,
        width: 200,
        transform: [{rotateX: rotate},{rotateY:rotate},{rotateZ:rotate}]
      }"
    />
  </view>
</template>

<script>
import { Animated, Easing } from "react-native";

export default {
  data() {
    return {
      rotate: 0,
      rotateInter: 0,
    };
  },
  methods: {
    rotarAnimacion: function () {
      Animated.timing(this.rotateInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.rotateInter.setValue(0);
        this.rotarAnimacion()
      });
    },
  },
  created() {
    //this.rotate = new Animated.Value(0)
    this.rotateInter = new Animated.Value(0);

    this.rotate = this.rotateInter.interpolate({
      inputRange: [0,1],
      outputRange: ["0deg","360deg"],
    });
  },
  mounted() {
    this.rotarAnimacion();
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