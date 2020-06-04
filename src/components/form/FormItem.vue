<template>
  <section class="wrapper">
    <div class="input_wrap">
      <label v-if="label" class="label" :style="{ width: labelWidth }">{{ label }}</label>
      <slot></slot>
    </div>
    <p v-if="errorMessage" class="error_msg" :style="{ paddingLeft: labelWidth }">
      {{ errorMessage }}
    </p>
  </section>
</template>

<script>
import Schema from "async-validator";

export default {
  name: "FormItem",
  inject: ["form"],
  props: {
    label: {
      type: String,
      default: ""
    },
    labelWidth: {
      type: String,
      default: ""
    },
    prop: String
  },
  data() {
    return {
      errorMessage: ""
    };
  },
  mounted() {
    this.$on("validate", () => {
      this.validate();
    });
  },
  methods: {
    validate() {
      const rules = this.form.rules[this.prop];
      const value = this.form.model[this.prop];

      const schema = new Schema({
        [this.prop]: rules
      });
      return schema.validate({ [this.prop]: value }, err => {
        if (err) {
          this.errorMessage = err[0].message;
        } else {
          this.errorMessage = "";
        }
      });
    }
  }
};
</script>
<style scoped lang="scss">
.wrapper {
  height: 50px;
}
.input_wrap {
  display: flex;
  align-items: center;
  font-size: 14px;
}
.error_msg {
  font-size: 14px;
  color: red;
  height: 20px;
  line-height: 20px;
}
</style>
