<template>
  <section class="form">
    <Form :model="model" :rules="rules" ref="loginForm">
      <form-item label="用户名：" prop="username" label-width="70px">
        <Input v-model="model.username" />
      </form-item>
      <form-item label="密码：" prop="password" label-width="70px">
        <Input v-model="model.password" type="password" />
      </form-item>
      <form-item>
        <button @click="onLogin">登录</button>
      </form-item>
    </Form>
  </section>
</template>

<script>
import Input from "./Input.vue";
import FormItem from "./FormItem.vue";
import Form from "./Form.vue";

export default {
  name: "index",
  data() {
    const validateUsername = (rule, value, callback) => {
      if (!value) {
        return callback(new Error("用户名必填"));
      } else if (value !== "admin") {
        callback(new Error("用户名错误 - admin"));
      } else {
        callback();
      }
    };
    const validatePassword = (rule, value, callback) => {
      if (!value) {
        return callback(new Error("密码必填"));
      } else if (value !== "123456") {
        callback(new Error("密码错误 - 123456"));
      } else {
        callback();
      }
    };
    return {
      model: {
        username: "",
        password: ""
      },
      rules: {
        username: [{ required: true, validator: validateUsername }],
        password: [{ required: true, validator: validatePassword }]
      }
    };
  },
  methods: {
    onLogin() {
      this.$refs.loginForm.validate(isValid => {
        if (isValid) {
          alert("success");
        } else {
          alert("failed");
        }
      });
    }
  },
  components: {
    Input,
    FormItem,
    Form
  }
};
</script>
<style scoped lang="scss">
.form {
  width: 300px;
  border: 1px solid #cccccc;
  border-radius: 5px;
  padding: 20px 15px;
  margin: 10px;
}
</style>
