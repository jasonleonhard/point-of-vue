<template>
  <view class="container">
    <view class="pad-top"> </view>

    <view class="flex-container outline wide">
      <text class="blanch outline pad size">
        Greetings {{usr}},
        {{ myInput }}
      </text>

      <touchable-opacity :on-press="onPressLearnMore" class="outline pad size2">
        <image class="img"
          :source="{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}" />
        <text class="blanch">Press Me</text>
        <image class="img"
          :source="{uri: 'https://vuejsexamples.com/favicon.png'}" />
      </touchable-opacity>
    </view>

    <text-input v-model="myInput" placeholder="type here" class="blanch outline pad"
      :style="{height: 40, width: '100%', borderWidth: 1, borderColor: 'white'}" />

    <scroll-view :style="{width: '100%'}">
      <touchable-opacity v-for="(country, index) in countries" :key="index"
                         class="outline countries flex-container"
                         :on-press="() => handleListTap(country)">
        <view>
          <image class="img2 " :source="{uri: country.imageSrc}" />
        </view>
        <view>
          <text class="blanch right pad-left">{{country.name}}</text>
        </view>
      </touchable-opacity>
    </scroll-view>

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
  .countries {
    /* color: #fff; */
    padding: 10;
    /* width: 100%; */
    /* text-align: left; */
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
    data() {
      return {
        usr: 'User',
        myInput: '',
        countries: [
          { name: "Australia", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/au.png"},
          { name: "Belgium", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/be.png"},
          { name: "Czech Republic", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/cz.png"},
          { name: "Germany", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/de.png"},
          { name: "Haiti", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ht.png"},
          { name: "Italy", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/it.png"},
          { name: "Japan", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/jp.png"},
          { name: "Romania", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ro.png"},
          { name: "Spain", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/es.png"},
          { name: "Switzerland", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ch.png"},
          { name: "USA", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/us.png"},
        ],
      }
    },
    methods: {
      onPressLearnMore() {
        alert(this.myInput)
      },
      onPressButton() {
        this.myInput = 'button clicked'
      },
      handleListTap(country) {
        console.log(country.name)
        alert(country.name)
      },
    }
  }
</script>
