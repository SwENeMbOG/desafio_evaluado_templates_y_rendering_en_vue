<template>
  <section class="result-section">
    <div :class="{ 'opaque': styles.isOpaque }" class="rectangle-container" :style="rectangleStyles">
      <div v-show="showText" class="text-content">
        {{ contentText }}
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    styles: Object,
    showText: Boolean,
    contentText: String
  },
  computed: {
    rectangleStyles() {
      return {
        backgroundColor: this.styles.backgroundColor,
        color: this.styles.color,
        borderRadius: `${this.styles.borderRadius}%`,
        fontFamily: this.styles.fontFamily,
        opacity: this.styles.isOpaque ? 0.5 : 1,
        fontSize: this.styles.fontSize,
        border: '0.125rem solid #000'
      };
    }
  }
};
</script>

<style>
.result-section {
  width: 70%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.rectangle-container {
  width: 100%;
  height: 18.75rem;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  position: relative;
}

.text-content {
  position: absolute;
}

.opaque {
  opacity: 0.5;
}
</style>
