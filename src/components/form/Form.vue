<template>
  <section>
    <slot></slot>
  </section>
</template>

<script>
export default {
  name: "Form",
  provide() {
    return {
      form: this
    };
  },
  props: {
    model: {
      type: Object,
      required: true
    },
    rules: {
      type: Object
    },
    labelWidth: {
      type: String,
      default: ""
    },
  },
  data() {
    return {};
  },
  methods: {
    validate(cb) {
      const result = this.$children.filter(child => child.prop).map(item => item.validate());
      Promise.all(result)
        .then(() => cb(true))
        .catch(() => cb(false));
    }
  }
};
</script>
<style scoped lang="scss"></style>
