<template>
  <view class="container">
    <view class="flex-container outline wrap full">
      <touchable-opacity v-for="(friend, index) in friends" :key="index"
                         class="outline friends flex-container pad"
                         :on-press="() => handleListTap(friend)">
        <view>
          <image class="img2 " :source="{uri: friend.imageSrc}" />
        </view>
        <view>
          <text class="blanch right pad-left">{{friend.name}}</text>
        </view>
      </touchable-opacity>
    </view>
    <text class="blanch pad outline bottom"
          :on-press='() => navigation.navigate("Main")'>Main</text>

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
        friends: []
      }
    },
    mounted() {
      fetch('https://jsonplaceholder.typicode.com/users')
        .then(response => response.json())
        .then((data) => {
          this.friends = data
        })
        console.log('FRIENDS1: ', this.friends)
    },
    methods: {
      handleListTap(friend) {
        // alert(JSON.stringify(friend))
        console.log(friend) // all
        alert(friend.company.name + '\n' + friend.phone + '\n' + friend.email)
      }
    }
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
  .outline {
    border-color: white;
    border-radius: 8;
    border-width: 1;
  }
  .wrap {
    flex-wrap: wrap;
  }
  .full {
    /* height: 95%; */
    height: 100%;
  }
  .bottom {
    position: absolute;
    bottom:20;
    left: 40%;
    /* justify-content: flex-end; */
  }
</style>
