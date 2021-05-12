<template>
  <div>Dialog 示例</div>

  <t-button @click="toggle">toggle</t-button>
  <t-dialog v-model:visible="dialogVisible">

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
    return {
      dialogVisible,
      toggle
    }
  }
}
</script>