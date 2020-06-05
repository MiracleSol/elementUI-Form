<template>
  <section>
    <input type="checkbox" :checked="checked" @change="onChange" />
  </section>
</template>

<script>
export default {
  name: "CheckBox",
  props: {
    checked: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {};
  },
  model: {
    prop: "checked",
    event: "change"
  },
  methods: {
    onChange(e) {
      this.$emit("change", e.target.checked)
    }
  }
};
</script>
<style scoped lang="scss"></style>
