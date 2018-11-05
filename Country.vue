<template>
  <view class="container">
    <view class="flex-container outline wide">
      <!-- greet feedback box, currently not in use -->
      <!-- <text class="blanch outline pad size">
        Greetings {{usr}},
        {{ myInput }}
      </text> -->

     <!-- not in use button -->
      <!-- <touchable-opacity :on-press="goToMain" class="outline pad size2">
        <image class="img"
          :source="{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}" />
        <text class="blanch">Press Me</text>
        <image class="img"
          :source="{uri: 'https://vuejsexamples.com/favicon.png'}" />
      </touchable-opacity> -->
    </view>

    <!-- input, currently not in use -->
    <!-- <text-input v-model="myInput" placeholder="type here" class="blanch outline pad"
      :style="{height: 40, width: '100%', borderWidth: 1, borderColor: 'white'}" /> -->

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

      <!-- list of results -->
      <touchable-opacity v-for="(post, index) in posts" :key="index"
                         class="outline posts flex-container"
                         :on-press="() => handleListTap(post)"
      >
        <view>
          <text class="blanch right pad-left">{{post.title}}</text>
          <text class="blanch right pad-left">{{post.snippet.replace(/<\/?[^>]+>/gi, '')}}</text>
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

<script>
  export default {
    props: {
      navigation: {
        type: Object
      }
    },
    data() {
      return {
        usr: 'User',
        myInput: '',
        posts: [],
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
      goToMain() {
        this.navigation.navigate("Main");
        // alert(this.myInput)
      },
      handleListTap(country) {
        // console.log(country.name)
        // alert(country.name)

        // alert(data)
        // alert(this.mounted())
        this.maybe(country)
      },
      maybe(country) {
      fetch('https://en.wikipedia.org/w/api.php?action=query&list=search&prop=info&inprop=url&utf8=&format=json&origin=*&srlimit=20&srsearch=' + country.name)
        // fetch('https://en.wikipedia.org/w/api.php?action=query&list=search&prop=info&inprop=url&utf8=&format=json&origin=*&srlimit=20&srsearch=' + country)
        // fetch('https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=' + country + '&format=json')
        // fetch('https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=' + country)
          .then(response => response.json())
          .then(data => {
            // better returns array but has not stripped out html
            this.posts = data.query.search
            // console.log(data.query.search)
          })
      },
    },
  }
</script>
