<template>
  <section>
    <input :value="value" @input="onInput" class="input" />
  </section>
</template>

<script>
export default {
  name: "Input",
  props: {
    value: {
      type: String,
      default: ""
    }
  },
  data() {
    return {};
  },
  methods: {
    onInput(e) {
      this.$emit("input", e.target.value);
      this.$parent.$emit("validate");
    }
  }
};
</script>
<style scoped lang="scss">
.input {
  width: 200px;
  height: 25px;
  border: 1px solid #414442;
  border-radius: 5px;
}
</style>
