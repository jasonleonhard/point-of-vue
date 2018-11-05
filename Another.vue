<template>
  <view class="container">
    <image
      :style="{width: '100%', height: '90%'}"
      :source="{uri: navigation.getParam('imageSrc')}"
    />
    <view class="flex-container" :style="{width: '90%', height: '10%'}">
      <view>
        <button color="white" title="back" :on-press="() => navigation.goBack()"/>
        <button color="white" title="show" :on-press="() => console.log(navigation.getParam('imageSrc'))"/>
      </view>
      <view class="pad">
        <text class="blanch">{{navigation.getParam('title')}}</text>
        <text class="blanch2">{{navigation.getParam('imageSrc')}}</text>
      </view>
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
  }
  .blanch {
    color: white;
    font-weight: bold;
  }
  .blanch2 {
    color: white;
  }
  .flex-container {
    flex-direction: row;
    align-items: center;
  }
  .pad {
    padding: 10;
    margin: 5;
  }
</style>
