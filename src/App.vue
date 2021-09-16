<template>
  <TheHeader title="Favourite Books" />
  <TheBooks />
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheBooks from './components/books/TheBooks.vue';
export default {
  name: 'App',
  components: {
    TheHeader,
    TheBooks,
  },
};
</script>
