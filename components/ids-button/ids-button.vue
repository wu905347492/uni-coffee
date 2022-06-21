<template>
  <button
    class="ids-btn"
    :class="[type ? 'ids-btn-' + type : 'ids-btn-primary', bold ? 'ids-btn-text-bold' : '', getShapeClass(shape)]"
    :hover-class="getHoverClass()"
    :style="{ width: width, height: height, lineHeight: height, fontSize: size, margin: margin }"
    :disabled="disabled"
    :form-type="formType"
    :open-type="openType"
    @getuserinfo="bindgetuserinfo"
    @getphonenumber="bindgetphonenumber"
    @contact="bindcontact"
    @error="binderror"
    @tap.stop="handleClick"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'idsButton',
  emits: ['click', 'getuserinfo', 'contact', 'getphonenumber', 'error'],
  props: {
    // 按钮主题色 [default, primary]
    type: {
      type: String,
      default: 'primary',
    },
    //形状 [circle, square]
    shape: {
      type: String,
      default: 'circle',
    },
    // 宽度 rpx或%
    width: {
      type: String,
      default: '100%',
    },
    //高度 rpx
    height: {
      type: String,
      default: '72rpx',
    },
    //字体大小 rpx
    size: {
      type: String,
      default: '32rpx',
    },
    bold: {
      type: Boolean,
      default: false,
    },
    margin: {
      type: String,
      default: '0',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    formType: {
      type: String,
      default: '',
    },
    openType: {
      type: String,
      default: '',
    },
    // 节流 300ms
    preventClick: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      time: 0,
    };
  },
  methods: {
    handleClick() {
      if (this.disabled) return;
      if (this.preventClick) {
        if (new Date().getTime() - this.time <= 300) return;
        this.time = new Date().getTime();
        setTimeout(() => {
          this.time = 0;
        }, 300);
      }
      this.$emit('click');
    },
    bindgetuserinfo({ detail = {} } = {}) {
      this.$emit('getuserinfo', detail);
    },
    bindcontact({ detail = {} } = {}) {
      this.$emit('contact', detail);
    },
    bindgetphonenumber({ detail = {} } = {}) {
      this.$emit('getphonenumber', detail);
    },
    binderror({ detail = {} } = {}) {
      this.$emit('error', detail);
    },
    getShapeClass(shape) {
      let className = '';
      if (shape == 'circle') {
        className = 'ids-circle';
      }
      return className;
    },
    getHoverClass() {
      let className = '';
      if (!this.disabled) {
        className = `ids-${this.type}-hover`;
      }
      return className;
    },
  },
};
</script>

<style lang="scss" scoped>
.ids-btn-primary {
  background-color: #333333 !important;
  color: #ffffff;
}

.ids-btn-white {
  background: #fff !important;
  color: #333 !important;
}

.ids-btn-black {
  background: #333 !important;
  color: #fff !important;
}

/* button start*/

.ids-btn {
  width: 100%;
  position: relative;
  border: 2rpx solid #333333 !important;
  border-radius: 8rpx;
  padding-left: 32rpx;
  padding-right: 32rpx;
  overflow: visible;
  display: flex;
  align-items: center;
  justify-content: center;
}

.ids-btn-flex-1 {
  flex: 1;
}

.ids-btn-text-bold {
  font-weight: 500;
}

.ids-primary-hover {
  background: mix(#333, #fff, 85%) !important;
  border-color: mix(#333, #fff, 85%) !important;
  color: mix(#333, #fff, 85%) !important;
}

/*圆角 */
.ids-circle {
  border-radius: 9999rpx;
}
</style>
