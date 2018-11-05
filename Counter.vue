<template>
  <view class="container">
    <!-- best version button changes itself -->
    <view class="outline flex-container">
      <button :title="String(count)" :onPress="btnClickIncrement" color="white"/>
    </view>
    
    <!-- alternate version button changes a text element -->
    <view class="outline flex-container wide">
      <text class="blanch pad outline">counter: {{ count }}</text>
      <button :onPress="btnClickIncrement" :title="title" color="white"/>
    </view>

    <text class="blanch pad outline wide" :on-press="() => navigation.navigate('Main')">Main</text>
  </view>
</template>

<script>
export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data() {
    return {
      count: 0,
      title: "tap here:"
    }
  },
  methods: {
    btnClickIncrement() {
      this.count = this.count +1
    }
  }
}
</script>


<style>
.blanch {
  color: white;
  font-weight: bold;
}
.pad {
  padding: 10;
  margin: 5;
}
.container {
  background-color: teal;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.countries {
  padding: 10;
}
.template {
  background-color: teal;
}
.outline {
  border-color: white;
  border-radius: 8;
  border-width: 1;
}
.img {
  width: 50;
  height: 50;
  margin-left: auto;
  margin-right: auto;
}
.img2 {
  width: 20;
  height: 20;
}
.right {
  margin-right: 8;
}
.left {
  margin-left: 8;
}
.center {
  text-align: right;
  text-align: left;
}
.flex-container {
  flex-direction: row;
  align-items: center;
}
.pad-left {
  padding-left: 10;
}
.size {
  height: 90%;
  width: 70%;
}
.size2 {
  height: 90%;
  width: 25%;
}
.wide {
  width: 100%;
}
</style>
