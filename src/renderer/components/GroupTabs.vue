<template>
  <div class="tabs">
    <div
      v-for="tab of tabs"
      :key="tab.value"
      :class="{tab: true, selected: modelValue === tab.value}"
      @click="$emit('update:modelValue', tab.value)"
    >{{tab.label}}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

type Tab = { label: string, value: string }

export default defineComponent({
  name: 'group-tabs',
  props: {
    modelValue: String,
    tabs: {
      type: Array as () => Tab[],
      required: true,
    }
  },
})
</script>

<style lang="scss" scoped>
.tabs {
  display: flex;
  background: var(--g-color-80);
  border-radius: var(--g-border-radius);
  border: 1px solid var(--g-color-70);
  margin-bottom: 16px;

  .tab {
    cursor: pointer;
    font-size: 14px;
    line-height: 2;
    padding: 0 1em;
    color: var(--g-color-20);
    border-radius: var(--g-border-radius);

    &:hover {
      background: var(--g-color-85);
    }

    &.selected {
      color: var(--g-color-0);
      font-weight: 500;
      background: var(--g-color-65);
    }
  }
}
</style>
