<template>
  <view class="center">
    <animated:view
      class="estatica"
      :style="{
        height: 200,
        width: 200,
        transform: [{scaleX: scale},{scaleY:scale}]
      }"
    />
  </view>
</template>

<script>
import { Animated, Easing } from "react-native";

export default {
  data() {
    return {
      scale: 0,
      scaleInter: 0,
    };
  },
  methods: {
    scaleAnimacion: function () {
      Animated.timing(this.scaleInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.scaleInter.setValue(0);
        this.scaleAnimacion()
      });
    },
  },
  created() {
    //this.scale = new Animated.Value(0)
    this.scaleInter = new Animated.Value(0);

    this.scale = this.scaleInter.interpolate({
      inputRange: [0,1],
      outputRange: [1,2],
    });
  },
  mounted() {
    this.scaleAnimacion();
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