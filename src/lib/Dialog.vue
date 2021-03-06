<template>
  <template v-if="visible">
    <teleport to="body">
      <div class="t-dialog-overlay" @click="handleClickOverlay"></div>
      <div class="t-dialog-wrapper">
        <div class="t-dialog">
          <header>
            {{ title }}
            <span class="t-dialog-close" @click="closeDialog"></span>
          </header>
          <main>
            <slot name="content"/>
          </main>
          <footer>
            <Button theme="primary" @click="handleOk">OK</Button>
            <Button @click="handleCancel">Cancel</Button>
          </footer>
        </div>
      </div>
    </teleport>
  </template>
</template>

<script lang="ts">
import Button from "./Button.vue";

export default {
  name: 't-dialog',
  components: {
    Button
  },
  props: {
    visible: {
      type: Boolean,
      default: false
    },
    closeOnClickOverlay: {
      type: Boolean,
      default: true
    },
    title: {
      type: String,
      default: '提示'
    },
    ok: Function
  },
  setup(props, context) {
    const closeDialog = () => {
      context.emit('update:visible', false)
    }
    const handleClickOverlay = () => {
      if (props.closeOnClickOverlay) {
        closeDialog()
      }
    }
    const handleOk = () => {
      if (!!props.ok?.()) {
        closeDialog()
      }
    }
    const handleCancel = () => {
      props.cancel?.()
      closeDialog()
    }
    return { closeDialog, handleClickOverlay, handleOk, handleCancel }
  }
};
</script>

<style lang="scss">
$radius: 4px;
$border-color: #d9d9d9;
.t-dialog {
  background: white;
  border-radius: $radius;
  box-shadow: 0 0 3px fade_out(black, 0.5);
  min-width: 15em;
  max-width: 90%;

  &-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: fade_out(black, 0.5);
    z-index: 10;
  }

  &-wrapper {
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 11;
  }

  > header {
    padding: 12px 16px;
    border-bottom: 1px solid $border-color;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 20px;
  }

  > main {
    padding: 12px 16px;
  }

  > footer {
    border-top: 1px solid $border-color;
    padding: 12px 16px;
    text-align: right;
  }

  &-close {
    position: relative;
    display: inline-block;
    width: 16px;
    height: 16px;
    cursor: pointer;

    &::before,
    &::after {
      content: '';
      position: absolute;
      height: 1px;
      background: black;
      width: 100%;
      top: 50%;
      left: 50%;
    }

    &::before {
      transform: translate(-50%, -50%) rotate(-45deg);
    }

    &::after {
      transform: translate(-50%, -50%) rotate(45deg);
    }
  }
}
</style>
