<template>
  <view>
    <button title="back" :on-press="() => navigation.goBack()"/>
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
