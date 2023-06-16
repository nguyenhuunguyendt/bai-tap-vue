<template>
  <button
    type="button"
    class="btn"
    :class="[colorButton ? colorButton : '']"
    @click="handleEmitData"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "CpButton",
  props: {
    colorButton: {
      type: String,
      default: "",
    },
    text: {
      type: String,
      default: "",
    },
    type: {
      type: String,
      default: "",
    },
  },
  methods: {
    handleEmitData(index) {
      if (this.type == "add") {
        return this.$emit("addPerson");
      }

      if (this.type == "delete") {
        return this.$emit("deletePerson", index);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
