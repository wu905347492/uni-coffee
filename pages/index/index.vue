<template>
  <view>
    <view>{{ page }}</view>
    <ids-button @click="handleClick" :preventClick="true">Dialog</ids-button>
    <ids-dialog :show="modal" @click="handleClick" title="提示" content="确定退出登录吗？"></ids-dialog>
    <view class="btn-box"><ids-button shape="circle" shadow @click="bDrawer">从底部弹出 Drawer</ids-button></view>
    <ids-drawer mode="bottom" :visible="bottomDrawer" @close="closeDrawer">
      <view class="tui-drawer__box"
        ><tui-button height="80rpx" type="green" shape="circle" @click="closeDrawer">关闭抽屉</tui-button></view
      >
    </ids-drawer>
    <view>
      <!-- <u-popup :show="show" @close="close" @open="open">
        <view>
          <text>出淤泥而不染，濯清涟而不妖</text>
        </view>
      </u-popup>
      <u-button @click="show = true">打开</u-button> -->
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      page: 'index',
      modal: false,
      bottomDrawer: false,
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
<style></style>
