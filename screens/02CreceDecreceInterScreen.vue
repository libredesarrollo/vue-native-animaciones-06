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
import { Animated, Easing } from "react-native";

export default {
  data() {
    return {
      growth: 0,
      growthInter: 0,
    };
  },
  methods: {
    crecerAnimacion: function () {
      Animated.timing(this.growthInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.growthInter.setValue(0);
        this.crecerAnimacion()
      });
    },
  },
  created() {
    //this.growth = new Animated.Value(0)
    this.growthInter = new Animated.Value(0);

    this.growth = this.growthInter.interpolate({
      inputRange: [0, 0.5, 0.7, 1],
      outputRange: [0, 600, 200 , 300],
    });
  },
  mounted() {
    this.crecerAnimacion();
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