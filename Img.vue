<template>
  <view class="container">
    <view class="pad-top"> </view>
    <image :style="{width: '100%', height: '100%'}"
      :source="{uri: navigation.getParam('imageSrc')}" />
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
