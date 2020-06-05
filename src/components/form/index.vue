<template>
  <section class="form">
    <Form :model="model" :rules="rules" ref="loginForm" label-width="70px">
      <form-item label="用户名：" prop="username">
        <Input v-model="model.username" />
      </form-item>
      <form-item label="密码：" prop="password">
        <Input v-model="model.password" type="password" />
      </form-item>
      <form-item label="记住密码：">
        <CheckBox v-model="model.remember"></CheckBox>
      </form-item>
      <form-item>
        <button class="btn" @click="onLogin">登录</button>
      </form-item>
    </Form>
  </section>
</template>

<script>
import Input from "./Input.vue";
import CheckBox from "./CheckBox.vue";
import FormItem from "./FormItem.vue";
import Form from "./Form.vue";
import Notice from "@/components/Notice";
import create from "@/utils/create.js";

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
        password: "",
        remember: false
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
        create(Notice, {
          title: "提示信息",
          message: isValid ? "登录成功" : "登录失败",
          duration: 1500
        }).show();
      });
    }
  },
  components: {
    Input,
    CheckBox,
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
.btn {
  padding: 5px 23px;
  border-radius: 10px;
  background-color: #409eff;
  border: 1px solid #409eff;
  color: #ffffff;
  font-size: 14px;
  &:hover {
    background-color: #0d80f3;
    border-color: #0d80f3;
  }
}
</style>
