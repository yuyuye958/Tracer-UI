<template>
  <h1>Dialog 示例</h1>

  <h2>示例1</h2>
  <t-button @click="toggle1">template方式</t-button>
  <t-dialog
      v-model:visible="dialogVisible"
      :closeOnClickOverlay="false"
      title="测试标题"
      :ok="ok"
      :cancel="cancel">
    <template v-slot:content>
      <strong>content</strong>
    </template>
  </t-dialog>

  <h2>示例2</h2>
  <t-button @click="toggle2">纯代码方式</t-button>
</template>

<script lang="ts">
import TDialog from '../lib/Dialog.vue'
import TButton from '../lib/Button.vue'
import { openDialog } from '../lib/openDialog'
import { ref } from 'vue'

export default {
  name: 'DialogDemo',
  components: {
    TDialog,
    TButton
  },
  setup() {
    const dialogVisible = ref(false)
    const toggle1 = () => {
      dialogVisible.value = !dialogVisible.value
    }
    const ok = () => {
      console.log('ok')
      return true
    }
    const cancel = () => {
      console.log('cancel')
    }

    const toggle2 = () => {
      openDialog({
        title: '示例2标题',
        content: '示例2内容',
        ok() {
          console.log('ok')
          return true
        },
        cancel() {
          console.log('cancel')
        }
      })
    }
    return {
      dialogVisible,
      ok,
      cancel,
      toggle1,
      toggle2
    }
  }
}
</script>
