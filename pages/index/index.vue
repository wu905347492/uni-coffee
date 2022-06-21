<template>
  <view>
    <view>{{ page }}</view>
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
