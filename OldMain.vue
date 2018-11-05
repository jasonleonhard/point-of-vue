<template>
  <view class="container">
    <!-- <view class="pad-top"> </view> -->
    <view class="flex-container outline wide">
      <text class="blanch outline pad size">
        Greetings {{usr}},
        {{ myInput }}
      </text>
      <touchable-opacity :on-press="searchButton" class="outline pad size2">
        <image class="img"
          :source="{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}" />
        <!-- <text class="blanch" :on-press="() => navigation.goBack()">Press Me</text> -->
        <!-- <text class="blanch" :on-press="() => navigation.goBack()">Press Me</text> -->
        <image class="img"
          :source="{uri: 'https://vuejsexamples.com/favicon.png'}" />
      </touchable-opacity>
    </view>

    <text-input v-model="myInput" placeholder="Search Here" class="blanch outline pad"
      :style="{height: 40, width: '100%', borderWidth: 1, borderColor: 'white'}" />

    <scroll-view :style="{width: '100%'}">
      <touchable-opacity v-for="(post, index) in posts" :key="index"
                         class="outline posts flex-container"
                         :on-press="() => handleListTap(post)">
        <view>
          <image class="img2 " :source="{uri: post.data.thumbnail}" />
        </view>
        <view>
          <text class="blanch right pad-left">{{post.data.title}}</text>
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
  .posts {
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
    props: {
      navigation: {
        type: Object
      }
    },
    mounted() {
      // fetch('https://reddit.com/r/aww.json')
      fetch('https://reddit.com/r/all.json')
        .then(response => response.json())
        .then(data => {
          this.posts = data.data.children
        })
    },
    data() {
      return {
        usr: 'User',
        myInput: '',
        posts: [],
      }
    },
    methods: {
    // jump to any route by name (Country, Main, Another, Bla, Img)
      searchButton() {
        this.navigation.navigate(this.myInput);
        // set input string in view
          // this.myInput = 'button clicked'
      },

    // nav to hard coded route
      // goToRoute() {
      //   // this.navigation.navigate("Main"); // returns to main
      //   // this.navigation.navigate("Another"); // returns self
      //   this.navigation.navigate("Img");
      // or by route and prop
      //   this.navigation.navigate("Img", {
      //      imageSrc: post.data.url,    // doesn't always work but often product
      //      title: post.data.title,
      //   },

      handleListTap(post) {
        // console.log(post.data.title)
        // alert(post.data.title)

        this.navigation.navigate("Another", { // img prop
          imageSrc: post.data.url,    // doesn't always work but often product
          title: post.data.title,
          thumb: post.data.thumbnail, // low res but url
          // imageSrc: post.data.preview.images[0].source.url
          // imageSrc:
        })
      },
    },
  }
</script>
