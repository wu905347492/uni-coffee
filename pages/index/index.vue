<template>
  <view>
    <view>{{ page }}</view>
    <view class="ids-hairline--bottom">aa</view>
    <ids-button></ids-button>
    <view class="test ids-multi-ellipsis--l2"
      >小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星小点星</view
    >
  </view>
</template>

<script>
export default {
  data() {
    return {
      page: 'index',
      modal: false,
      bottomDrawer: false,
      time: 30 * 60 * 60 * 1000,
      timeData: {},
    };
  },

  computed: {},

  methods: {
    handleClick() {
      this.modal = !this.modal;
    },
    bDrawer() {
      this.bottomDrawer = true;
    },
  },

  onReady() {},
  onLoad() {
    console.log('onload');
  },
  onShow() {
    console.log('show');
  },
};
</script>
<style>
.test {
  width: 400rpx;
}
.van-count-down {
  margin: 0 16px 10px;
}
.item {
  background-color: #1989fa;
  border-radius: 2px;
  color: #fff;
  display: inline-block;
  font-size: 12px;
  margin-right: 5px;
  text-align: center;
  width: 22px;
}
</style>
