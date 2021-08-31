<template>
  <teleport to="body">
    <div class="background" @click="$emit('close')"></div>
    <dialog open>
      <header>
        <slot name="header"> </slot>
      </header>
      <section>
        <slot></slot>
      </section>
      <div class="close">
        <slot name="close"></slot>
      </div>
    </dialog>
  </teleport>
</template>

<script>
export default {
  emits: ['close'],
};
</script>

<style scoped>
.background {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.75);
  z-index: 10;
}

dialog {
  position: fixed;
  top: 20vh;
  left: 10%;
  width: 80%;
  z-index: 100;
  border-radius: 12px;
  border: none;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 0;
  margin: 0;
  overflow: hidden;
}

header {
  background-color: #aa2ab2;
  color: white;
  width: 100%;
  padding: 1rem;
}

section {
  padding: 1rem;
}

.close {
  padding: 1rem;
  display: flex;
  justify-content: flex-end;
  margin: 0;
}

@media (min-width: 768px) {
  dialog {
    left: calc(50% - 20rem);
    width: 40rem;
  }
}
</style>
