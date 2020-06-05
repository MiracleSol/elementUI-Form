<template>
  <div class="box" v-if="isShow">
    <h3 class="title">{{ title }}</h3>
    <p class="box-content">{{ message }}</p>
  </div>
</template>

<script>
export default {
  name: "notice",
  props: {
    title: {
      type: String,
      default: ""
    },
    message: {
      type: String,
      default: ""
    },
    duration: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      isShow: false
    };
  },
  methods: {
    show() {
      this.isShow = true;
      setTimeout(() => {
        this.hide();
      }, this.duration);
    },
    hide() {
      this.isShow = false;
      this.remove();
    }
  }
};
</script>
<style scoped lang="scss">
.box {
  position: fixed;
  top: 50px;
  left: 0;
  right: 0;
  width: 300px;
  padding: 15px 20px;
  border: 1px solid #dddddd;
  background-color: #dddddd;
  border-radius: 5px;
  text-align: center;
  margin: 0 auto;
  .title {
    font-size: 20px;
    padding-bottom: 20px;
    font-weight: 600;
  }
  .box-content {
    width: 100%;
    box-sizing: border-box;
    font-size: 14px;
    text-align: center;
  }
}
</style>
