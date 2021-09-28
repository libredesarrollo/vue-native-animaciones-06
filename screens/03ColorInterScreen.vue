<template>
  <view class="center">
    <animated:view
      class="estatica"
      :style="{
        height: 200,
        width: 200,
        borderRadius: 200,
        backgroundColor: color
      }"
    />
  </view>
</template>

<script>
import { Animated, Easing } from "react-native";

export default {
  data() {
    return {
      color: 0,
      colorInter: 0,
    };
  },
  methods: {
    colorAnimacion: function () {
      Animated.timing(this.colorInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.colorInter.setValue(0);
        this.colorAnimacion()
      });
    },
  },
  created() {
    //this.color = new Animated.Value(0)
    this.colorInter = new Animated.Value(0);

    this.color = this.colorInter.interpolate({
      inputRange: [0, 0.5, 1],
      outputRange: ["rgb(255,0,0)", "rgb(0,255,0)" , "rgb(0,0,255)"],
    });
  },
  mounted() {
    this.colorAnimacion();
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