<script>
export default {
  name: "CustomButton",
  props: {
    label: {
      type: String,
      default: "Click Me",
    },

    download: {
      type: Boolean,
      default: true,
    },
    fileUrl: {
      type: String,
      default: "",
    },
    fileName: {
      type: String,
      default: "file.txt",
    },
  },
  methods: {
    handleClick() {
      this.$emit("click");
    },
  },
};
</script>

<template>
  <div class="button-body">
    <a
      v-if="download"
      :href="fileUrl"
      :download="fileName"
      :class="['custom-button', colorClass]"
    >
      {{ label }}
    </a>

    <button v-else :class="['custom-button', colorClass]" @click="handleClick">
      {{ label }}
    </button>
  </div>
</template>

<style scoped>
.custom-button {
  text-decoration: none;
  display: inline-block;
  text-align: center;
  padding: 10px 20px;
  border: 2px solid;
  border-radius: 5px;
  border-color: #f4a261;
  font-size: 1rem;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s ease, color 0.3s ease;
  background-color: #f4a261;
  color: #ffffff;
}

.custom-button:hover {
  background-color: #222831;
}
</style>
