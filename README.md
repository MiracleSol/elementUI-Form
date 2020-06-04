# 模仿 Element 的表单组件

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

#### Input 组件实现基本要点
1. 自定义组件要实现 v-model 必须实现 :value 和 @input
2. 

#### FormItem 组件实现基本要点
1. 给 Input 预留插槽 - slot
2. 使用 provide/inject 接收 form 传递过来的数据
3. 能够进行校验
  - 使用 async-validator 进行校验

#### Form 组件实现基本要点
1. 给 FormItem 预留插槽 - slot
2. 使用 provide/inject 传递 form 实例给后代

#### 注意;
- provide/inject 能用于祖代和后代之间传递数据，只能是祖代=>后代，不能反过来

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