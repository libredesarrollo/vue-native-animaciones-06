<template>
  <view class="center">
    <animated:view
      class="estatica"
      :style="{
        height: growth,
        width: growth,
        transform: [{translateX: translate},{translateY:translate}, {scaleX: scale},{scaleY:scale}],
        backgroundColor: color,
        transform: [
          { rotateX: rotate },
          { rotateY: rotate },
          { rotateZ: rotate },
        ],
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
      growth: 0,
      growthInter: 0,
      rotate: 0,
      rotateInter: 0,
            translate: 0,
      translateInter: 0,
            scale: 0,
      scaleInter: 0,
    };
  },
  methods: {
    paraleloAnimacion: function () {
      Animated.parallel([
        this.colorAnimacion(),
        this.crecerAnimacion(),
        this.rotarAnimacion(),
        this.transladaAnimacion(),
        this.scaleAnimacion()
      ]);
    },
    colorAnimacion: function () {
      Animated.timing(this.colorInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.colorInter.setValue(0);
        this.colorAnimacion();
      });
    },
    crecerAnimacion: function () {
      Animated.timing(this.growthInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.growthInter.setValue(0);
        this.crecerAnimacion();
      });
    },
    rotarAnimacion: function () {
      Animated.timing(this.rotateInter, {
        toValue: 1,
        duration: 2000,
        easing: Easing.linear,
      }).start(() => {
        this.rotateInter.setValue(0);
        this.rotarAnimacion();
      });
    },
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
    //this.color = new Animated.Value(0)
    this.colorInter = new Animated.Value(0);

    this.color = this.colorInter.interpolate({
      inputRange: [0, 0.3, 0.6, 1],
      outputRange: [
        "rgb(255,0,0)",
        "rgb(0,255,0)",
        "rgb(0,0,255)",
        "rgb(255,0,0)",
      ],
    });

    this.growthInter = new Animated.Value(0);

    this.growth = this.growthInter.interpolate({
      inputRange: [0, 0.5, 1],
      outputRange: [10, 600, 10],
    });

    this.rotateInter = new Animated.Value(0);

    this.rotate = this.rotateInter.interpolate({
      inputRange: [0, 1],
      outputRange: ["0deg", "360deg"],
    });

     this.translateInter = new Animated.Value(0);

    this.translate = this.translateInter.interpolate({
      inputRange: [0,1],
      outputRange: [0,150],
    });

       this.scaleInter = new Animated.Value(0);

    this.scale = this.scaleInter.interpolate({
      inputRange: [0,1],
      outputRange: [1,2],
    });
  },
  mounted() {
    this.paraleloAnimacion();
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