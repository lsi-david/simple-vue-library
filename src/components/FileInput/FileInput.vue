<template>
  <label
    @dragover.prevent
    @dragleave.prevent
    @dragover="onDragOver"
    @dragleave="onDragLeave"
    @drop="onDrop"
    class="file-input"
    :id="id"
    :style="{
      width: `${width}`,
      height: `${height}`,
    }"
  >
    <i class="icon-upload fas fa-cloud-upload-alt"></i>
    <span class="text-base"
      >Drag and drop your file or click here to upload</span
    >
    <input
      ref="fileUploader"
      @click="resetFileInput"
      @change="onChange"
      type="file"
      class="hidden"
    />
  </label>
</template>

<script>
export default {
  name: 'FileInput',
  props: {
    id: String,
    width: String,
    height: String,
    onChange: {
      type: Function,
      required: true,
      default() {
        return () => true;
      },
    },
    onDrop: {
      type: Function,
      required: true,
      default() {
        return () => true;
      },
    },
  },
  methods: {
    resetFileInput() {
      this.$refs.fileUploader.value = '';
    },
    onDragOver() {
      document.getElementById(this.id).classList.add('bg-green-300');
    },
    onDragLeave() {
      document.getElementById(this.id).classList.remove('bg-green-300');
    },
  },
};
</script>

<style scoped>
.bg-green {
  background-color: rgba(110, 231, 183, 0.8);
}

.file-input {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 7rem;
  background-color: none;
  color: black;
  border-radius: 0.75rem;
  letter-spacing: 0.025em;
  text-transform: uppercase;
  border: 1px dashed black;
  cursor: pointer;
}

.file-input:hover {
  background-color: rgba(110, 231, 183, 0.8);
}

.hidden {
  opacity: 0;
}

.icon-upload {
  font-size: 2.5rem;
}

.text-base {
  text-align: center;
  margin-top: 10px;
  line-height: 1.5;
  font-size: calc(8px + (16 - 8) * ((100vw - 300px) / (1600 - 300)));
}
</style>
