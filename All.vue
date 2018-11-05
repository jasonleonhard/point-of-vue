<template>
  <view class="container">
    <scroll-view class="wide">

      <!-- <button title="back" :on-press="() => navigation.goBack()"/> -->

      <!-- reddit related -->
      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Main")'>Main</text>
      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Reddit")'>Reddit</text>
      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("ShittyRobots")'>ShittyRobots</text>
      <!-- <text class="blanch pad outline"
            :on-press='() => navigation.navigate("OldMain")'>OldMain</text> -->

      <!-- <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Another")'>Another</text> -->
      <!-- <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Img")'>Img</text> -->

      <!-- wikipedia and local data -->
      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Country")'>Country</text>

      <!-- general purpose -->
      <!-- <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Bla")'>Bla</text> -->

      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Friends")'>Friends</text>

      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("BindThem")'>BindThem</text>

      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Counter")'>Counter</text>

      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("WatchMe")'>WatchMe</text>

      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("Counter")'>Counter</text>

      <text class="blanch pad outline"
            :on-press='() => navigation.navigate("External")'>External</text>
    </view>

  </view>
</template>

<script>
  export default {
    props: {
      navigation: {
        type: Object
      }
    },
  }
</script>

<style>
  .container {
    background-color: teal;
    align-items: center;
    justify-content: center;
    flex: 1;
  }
  .blanch {
    color: white;
    font-weight: bold;
  }
  .pad {
    padding: 10;
    margin: 5;
  }
  .outline {
    border-color: white;
    border-radius: 8;
    border-width: 1;
  }
  .wide {
    width: 100%;
  }

</style>
