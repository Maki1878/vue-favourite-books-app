<template>
  <button :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ['mode'],
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #aa2ab2;
  border: 1px solid #4d2b26;
  color: white;
  border-radius: 20px;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #8d1a91;
  border-color: #270041;
}

.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #ca93ca65;
}
</style>
