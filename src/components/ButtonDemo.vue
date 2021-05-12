<template>
  <h1>Button 示例</h1>
  <h2>按钮类型</h2>
  <div>
    <t-button @click="onClick">默认按钮</t-button>
    <t-button theme="primary">主要按钮</t-button>
    <t-button theme="success">成功按钮</t-button>
    <t-button theme="warning">警告按钮</t-button>
    <t-button theme="info">信息按钮</t-button>
    <t-button theme="danger">危险按钮</t-button>
    <t-button theme="text">文字按钮</t-button>
  </div>
  <h2>尺寸</h2>
  <div>
    <t-button disabled>默认大小</t-button>
    <t-button size="small">中等按钮</t-button>
    <t-button size="mini">小型按钮</t-button>
  </div>
  <h2>加载中</h2>
  <div>
    <t-button loading>Loading...</t-button>
  </div>
  <h2>禁用</h2>
  <div>
    <t-button disabled>禁用</t-button>
  </div>
</template>

<script lang="ts">
import TButton from "../lib/Button.vue";

export default {
  name: 'ButtonDemo',
  components: { TButton },
  setup() {
    const onClick = () => {
      console.log('test')
    }
    return { onClick }
  }
}
</script>
<style lang="scss" scoped>
::v-deep .t-button {
  margin-top: 8px;
}
</style>