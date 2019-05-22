<template>
  <div :style="`font-size: ${size}px`">{{text}}</div>
</template>

<script>
/**
 * @desc 根据内容自适应字号
 * @param {string} [text] - 显示的内容
 * @param {number} [maxFontSize] - 最大字号
 *
 * @example
 * <div style="display: inline-block;width: 100px;">
 *   <autofontsize text="这是文字" :maxFontSize="20"></autofontsize>
 * </div>
 */
export default {
  name: 'auto-font-size',

  props: {
    text: {
      default: '',
    },
    maxFontSize: {
      default: 26,
    },
  },

  data() {
    return {
      size: 14,
    };
  },

  watch: {
    text(cur) {
      this.calcFontSize();
    },
  },

  methods: {
    calcFontSize() {
      const text = this.text || '';
      const width = this.$el.clientWidth;
      let size = parseInt(width / text.length) || '';
      console.log(width, text.length, size);
      size > this.maxFontSize && (size = this.maxFontSize);
      this.size = size;
    },
  },

  mounted() {
    this.calcFontSize();
  },

};
</script>
