<script lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import SlotComponent from './components/SlotComponent.vue'

export default {
  components: {HelloWorld, SlotComponent},
}
</script>

<template>
<div>
  <HelloWorld :features="{foo: true}" />
  <SlotComponent>
    <template v-slot="props"><span>{{ props.value }}</span> </template>
    <template #oneThing="props"><span>{{ props.value }}</span> </template>
  </SlotComponent>
</div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
