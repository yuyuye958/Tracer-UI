<template>
  <button class="t-button" :class="classes" :disabled="disabled">
    <span v-if="loading" class="t-loading"></span>
    <span><slot/></span>
  </button>
</template>

<script lang="ts">
import { computed } from "vue";

export default {
  name: 't-button',
  props: {
    theme: {
      type: String,
      default: 'default'
    },
    size: {
      type: String,
      default: 'normal'
    },
    loading: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  setup(props) {
    const { theme, size } = props
    const classes = computed(() => {
      return {
        [`t-button-${theme}`]: theme,
        [`t-button-${size}`]: size,
      }
    })
    return { classes }
  }
}
</script>

<style lang="scss">
@keyframes spin {
  0% {
    transform: rotate(0);
  }
  100% {
    transform: rotate(360deg);
  }
}

.t-button {
  display: inline-block;
  line-height: 1;
  white-space: nowrap;
  cursor: pointer;
  color: #606266;
  text-align: center;
  box-sizing: border-box;
  outline: none;

  &[disabled] {
    cursor: not-allowed;
    color: grey;
  }

  > .t-loading {
    width: 14px;
    height: 14px;
    display: inline-block;
    margin-right: 4px;
    border-radius: 8px;
    border-color: blue blue blue transparent;
    border-style: solid;
    border-width: 2px;
    animation: spin 1s infinite linear;
  }

  > span {
    display: inline-block;
    vertical-align: middle;
  }

  margin: 0;
  transition: .1s;
  font-weight: 500;
  font-size: 14px;
  border-radius: 4px;

  &.t-button-default {
    background: #fff;
    border: 1px solid #dcdfe6;

    &:hover, &:focus {
      color: #222831;
      border-color: #222831;
      background-color: #eeeeee;
    }
  }

  &.t-button-primary {
    background: #00adb5;
    border: 1px solid #393e46;
    color: #eeeeee;

    &:hover, &:focus {
      color: #eeeeee;
      border-color: #222831;
      background-color: #40babf;
    }
  }

  &.t-button-success {
    background: #4ecca3;
    border: 1px solid #393e46;
    color: #eeeeee;

    &:hover, &:focus {
      color: #eeeeee;
      border-color: #222831;
      background-color: #6be3bc;
    }
  }

  &.t-button-danger {
    background: #d72323;
    border: 1px solid #d72323;
    color: #eeeeee;

    &:hover, &:focus {
      color: #eeeeee;
      border-color: #dd5656;
      background-color: #dd5656;
    }
  }

  &.t-button-info {
    background: #52616b;
    border: 1px solid #393e46;
    color: #eeeeee;

    &:hover, &:focus {
      color: #eeeeee;
      border-color: #222831;
      background-color: #6c777d;
    }
  }

  &.t-button-warning {
    background: #fce38a;
    border: 1px solid #393e46;
    color: #4a4444;

    &:hover, &:focus {
      color: #8e8282;
      border-color: #222831;
      background-color: #f7e4a4;
    }
  }

  &.t-button-text {
    background: #fff;
    border: 0;
    color: #4a4444;

    &:hover, &:focus {
      > span {
        color: #8e8282;
        border-color: #222831;
        background-color: #f7e4a4;
      }
    }
  }

  &.t-button-normal {
    padding: 12px 20px;
  }

  &.t-button-small {
    padding: 10px 20px;
    font-size: 14px;
    border-radius: 4px;
  }

  &.t-button-mini {
    padding: 9px 15px;
    font-size: 12px;
    border-radius: 3px;
  }
}
</style>