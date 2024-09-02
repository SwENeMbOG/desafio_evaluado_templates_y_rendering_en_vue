<template>
  <div id="app" class="container">
    <FormSection @update="updateStyles" @updateText="updateContentText" @toggleText="toggleText" />
    <ResultSection :styles="styles" :showText="showText" :contentText="contentText" />
  </div>
</template>

<script>
import FormSection from './components/FormSection.vue';
import ResultSection from './components/ResultSection.vue';

export default {
  components: {
    FormSection,
    ResultSection
  },
  data() {
    return {
      showText: true,
      contentText: '',
      styles: {
        backgroundColor: '#ffffff',
        color: '#000000',
        borderRadius: 0,
        fontFamily: 'Arial',
        fontSize: '1rem',
        isOpaque: false
      }
    };
  },
  methods: {
    updateStyles(newStyles) {
      this.styles = { ...this.styles, ...newStyles };
    },
    updateContentText(newText) {
      this.contentText = newText;
    },
    toggleText(value) {
      this.showText = value;
    }
  }
};
</script>

<style>
.container {
  display: flex;
}
</style>
