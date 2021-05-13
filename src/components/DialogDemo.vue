<template>
  <div>Dialog 示例</div>

  <t-button @click="toggle">toggle</t-button>
  <t-dialog
      v-model:visible="dialogVisible"
      title="测试标题"
      :ok="ok">
    <div>内容1</div>
    <div>内容2</div>
  </t-dialog>
</template>

<script lang="ts">
import TDialog from '../lib/Dialog.vue'
import TButton from '../lib/Button.vue'
import { ref } from 'vue'

export default {
  name: 'DialogDemo',
  components: {
    TDialog,
    TButton
  },
  setup() {
    const dialogVisible = ref(false)
    const toggle = () => {
      dialogVisible.value = !dialogVisible.value
    }
    const ok = () => {
      console.log('ok')
      return true
    }
    return {
      dialogVisible,
      toggle,
      ok
    }
  }
}
</script>