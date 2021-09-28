<template>
  <app-navigator></app-navigator>
</template>

<script>
import {
  createAppContainer,
  createStackNavigator,
} from "vue-native-router";

import CreceScreen from "./screens/01CreceScreen.vue";
import CreceDecreceInterScreen from "./screens/02CreceDecreceInterScreen";
import ColorInterScreen from "./screens/03ColorInterScreen";
import DetailsScreen from "./screens/DetailsScreen";
import ParaleloScreen from "./screens/04ParaleloScreen";
import RotarInterScreen from "./screens/05RotarInterScreen";
import TranslacionInterScreen from "./screens/06TranslacionInterScreen";
import EscalarInterScreen from "./screens/07EscalarInterScreen";

const StackNavigator = createStackNavigator(
  {
    Crece: CreceScreen,
    CreceDecreceInter: CreceDecreceInterScreen,
    ColorInter: ColorInterScreen,
    Details: DetailsScreen,
    Paralelo: ParaleloScreen,
    RotarInter: RotarInterScreen,
    TranslacionInter: TranslacionInterScreen,
    EscalarInter: EscalarInterScreen,
    
  },
  {
    initialRouteName: 'Paralelo',
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { AppNavigator },
}
</script>