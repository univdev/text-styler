<style lang="less" scoped>
  .github-button {
    .icon {
      font-size: 24px;
    }
  }
</style>

<template>
  <el-button
    v-bind="{ ...$attrs, ...$props }"
    :color="color"
    class="github-button"
    native-type="button"
    circle
  >
    <i class="icon mdi mdi-github"/>
  </el-button>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';

export default defineComponent({
  props: {
    color: {
      type: String as PropType<string>,
      required: false,
      default: '#171515',
    },
  },
});
</script>
