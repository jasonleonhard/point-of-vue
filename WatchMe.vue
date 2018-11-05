<template>
  <view class="container">
    <!-- <view class="pad-top"> </view> -->
    <view class="flex-container outline wide">
      <text class="blanch outline pad size">
        Greetings {{usr}},
        Go to {{ myInput }}
      </text>
      <touchable-opacity :on-press="searchButton" class="outline pad size2">
        <image class="img"
          :source="{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}" />
        <text class="blanch">Press Me</text>
        <image class="img"
          :source="{uri: 'https://vuejsexamples.com/favicon.png'}" />
      </touchable-opacity>
    </view>
    <text-input v-model="myInput" placeholder="Search Here" class="blanch outline pad"
      :style="{height: 40, width: '100%', borderWidth: 1, borderColor: 'white'}" />
  </view>
</template>

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
  .posts {
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
    /* text-align: right; */
    /* text-align: left; */
  }
  .left {
    margin-left: 8;
  }
  .flex-container {
    flex-direction: row;
    align-items: center;
  }
  .pad-left {
    padding-left: 10;
  }
  .pad-top {
    padding-top: 50;
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

<script>
  export default {
    props: {
      navigation: {
        type: Object
      }
    },
    watch: {
      count(actualCount) {
        console.log(actualCount)
      }
    },
    data() {
      return {
        usr: 'User',
        myInput: '',
      }
    },
    methods: {
    // jump to any route by name (Country, Main, Another, Bla, Img)
      searchButton() {
        this.navigation.navigate(this.myInput);
      },
      handleListTap(post) {

        this.navigation.navigate("Another", { // img prop
          imageSrc: post.data.url,    // doesn't always work but often product
          title: post.data.title,
          thumb: post.data.thumbnail, // low res but url
        })
      },
    },
  }
</script>
