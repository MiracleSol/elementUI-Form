# 模仿 Element 的表单组件 + 弹框组件

### 表单组件实现
- Input 组件
  - 绑定数据模型- v-model
  - 通知 FormItem 执行校验
- FormItem 组件
  - 显示标签名字 - lable
  - 执行校验 - prop
  - 显示校验结果
- Form 组件
  - 管理数据模型 - model
  - 校验规则定义 - rules
  - 全局校验 - validate

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```