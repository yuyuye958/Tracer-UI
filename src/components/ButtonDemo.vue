<template>
  <div>Button 示例</div>
  <div>
    <Button @click="onClick">Button1</Button>
    <Button theme="button" @click="onClick">Button2</Button>
    <Button theme="link" @click="onClick">Button3</Button>
    <Button theme="text" @click="onClick">Button4</Button>
  </div>
</template>
<script lang="ts">
import Button from "../lib/Button.vue";

export default {
  components: { Button },
  setup() {
    const onClick = () => {
      console.log('test')
    }
    return { onClick }
  }
};
</script>