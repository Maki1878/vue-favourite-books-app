<template>
  <ul>
    <BookItem
      v-for="book in books"
      :key="book.id"
      :id="book.id"
      :title="book.title"
      :author="book.author"
      :description="book.description"
      :link="book.link"
    />
  </ul>
</template>

<script>
import BookItem from './BookItem.vue';
export default {
  props: ['books'],
  components: {
    BookItem,
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
