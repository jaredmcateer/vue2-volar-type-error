<script lang="ts">
import { defineComponent, PropType } from '@vue/composition-api';
export default defineComponent({ });
</script>

<template>
  <div>
    <slot name="oneThing" :value="'Hello World'"></slot>
    <slot :value="'Hello World'"></slot>
  </div>
</template>
