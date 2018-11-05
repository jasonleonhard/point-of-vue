<template>
  <app-navigation></app-navigation>
</template>

<script>
import { StackNavigator } from "vue-native-router"
// import { DrawerNavigator } from "vue-native-router"
import AllScreen from './All'

import MainScreen from './Main'
import AnotherScreen from './Another'
import CountryScreen from './Country'

import BlaScreen from './Bla'
import ImgScreen from './Img'
import RedditScreen from './Reddit'
import ShittyRobotsScreen from './ShittyRobots'

import FriendsScreen from './Friends'
import BindThemScreen from './BindThem'
import WatchMeScreen from './WatchMe'
import CounterScreen from './Counter'

import ExternalScreen from './External'

const AppNavigation = StackNavigator(
// const AppNavigation = DrawerNavigator(
  {
    Main: MainScreen,
    Reddit: RedditScreen,
    ShittyRobots: ShittyRobotsScreen,
    Another: AnotherScreen,
    Img: ImgScreen,

    All: AllScreen,
    Bla: BlaScreen,
    BindThem: BindThemScreen,
    External: ExternalScreen,
    Counter: CounterScreen,
    Country: CountryScreen,
    Friends: FriendsScreen,
    WatchMe: WatchMeScreen,
  },
  {
    initialRouteName: 'Main',
    // initialRouteName: 'All',
    // initialRouteName: 'Friends',
    // initialRouteName: 'External',
    // initialRouteName: 'Country',
  }
)

export default {
  components: { AppNavigation }
}
</script>
