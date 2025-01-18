<script setup lang="ts">
const props = defineProps<{
  type?: 'filled' | 'outlined'
  mode?: 'dark' | 'light'
}>()
</script>

<template>
  <button :class="props.type === 'outlined' ? 'button-outlined' : 'button-filled'">
    <slot></slot>
  </button>
</template>

<style lang="css" scoped>
.button-filled {
  background-color: black;
  color: white;
  border: none;
  padding: 1rem 2rem;

  &:hover {
    background-color: rgb(61, 61, 61);
    cursor: pointer;
  }
}

.button-outlined {
  background-color: transparent;
  border: 2px solid black;
  color: white;
  padding: 1rem;

  &:hover {
    background-color: black;
    cursor: pointer;
  }
}
</style>
