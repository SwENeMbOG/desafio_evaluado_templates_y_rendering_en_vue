<template>
  <section class="form-section">
    <form>
      <div>
        <label for="bgColor">Color de fondo</label>
        <input v-model="localStyles.backgroundColor" type="text" id="bgColor" @input="emitUpdate" />
      </div>

      <div>
        <label for="textColor">Color de texto</label>
        <input v-model="localStyles.color" type="text" id="textColor" @input="emitUpdate" />
      </div>

      <div>
        <label for="showText">Mostrar texto</label>
        <input v-model="localShowText" type="checkbox" id="showText" @change="emitToggleText" />
      </div>

      <div>
        <label for="borderRadius">Borde</label>
        <input v-model.number="localStyles.borderRadius" type="range" id="borderRadius" min="0" max="50" @input="emitUpdate" />
      </div>

      <div>
        <label for="content">Contenido textual</label>
        <input v-model="localContentText" type="text" id="content" @input="emitTextUpdate" />
      </div>

      <div>
        <label for="fontFamily">Tipografía</label>
        <select v-model="localStyles.fontFamily" id="fontFamily" @change="emitUpdate">
          <option v-for="font in fontOptions" :key="font" :value="font">{{ font }}</option>
        </select>
      </div>

      <div>
        <label for="opacity">Opaco</label>
        <input v-model="localStyles.isOpaque" type="checkbox" id="opacity" @change="emitUpdate" />
      </div>

      <div>
        <label>Tamaño de letra</label>
        <div>
          <input v-model="localStyles.fontSize" type="radio" id="small" value="0.75rem" @change="emitUpdate" />
          <label for="small">Pequeño</label>
          <input v-model="localStyles.fontSize" type="radio" id="medium" value="1rem" @change="emitUpdate" />
          <label for="medium">Mediano</label>
          <input v-model="localStyles.fontSize" type="radio" id="large" value="1.25rem" @change="emitUpdate" />
          <label for="large">Grande</label>
        </div>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  data() {
    return {
      localShowText: true,
      localContentText: '',
      localStyles: {
        backgroundColor: '#ffffff',
        color: '#000000',
        borderRadius: 0,
        fontFamily: 'Arial',
        fontSize: '1rem',
        isOpaque: false
      },
      fontOptions: ['Arial', 'Times New Roman', 'Courier New']
    };
  },
  methods: {
    emitUpdate() {
      this.$emit('update', this.localStyles);
    },
    emitTextUpdate() {
      this.$emit('updateText', this.localContentText);
    },
    emitToggleText() {
      this.$emit('toggleText', this.localShowText);
    }
  }
};
</script>

<style>
.form-section {
  background-color: #2f4f4f;
  padding: 1.25rem;
  width: 30%;
}
</style>
