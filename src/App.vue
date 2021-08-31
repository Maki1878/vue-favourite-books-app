<template>
  <TheHeader title="Favourite Books" />
  <TheNavbar />
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheNavbar from './components/books/TheBooks.vue';
export default {
  name: 'App',
  components: {
    TheHeader,
    TheNavbar,
  },
};
</script>
