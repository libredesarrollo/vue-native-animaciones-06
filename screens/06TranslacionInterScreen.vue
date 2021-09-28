<template>
  <view class="center">
    <animated:view
      class="estatica"
      :style="{
        height: 200,
        width: 200,
        transform: [{translateX: translate},{translateY:translate}]
      }"
    />
  </view>
</template>

<script>
import { Animated, Easing } from "react-native";

export default {
  data() {
    return {
      translate: 0,
      translateInter: 0,
    };
  },
  methods: {
    transladaAnimacion: function () {
      Animated.timing(this.translateInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.translateInter.setValue(0);
        this.transladaAnimacion()
      });
    },
  },
  created() {
    //this.translate = new Animated.Value(0)
    this.translateInter = new Animated.Value(0);

    this.translate = this.translateInter.interpolate({
      inputRange: [0,1],
      outputRange: [0,150],
    });
  },
  mounted() {
    this.transladaAnimacion();
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