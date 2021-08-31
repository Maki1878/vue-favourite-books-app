<template>
  <BaseCard class="header">
    <BaseButton
      class="header-button"
      @click="setSelectedTab('favourite-books')"
      :mode="favouriteBooksButtonMode"
      >Favourite Books</BaseButton
    >
    <BaseButton class="header-button" @click="setSelectedTab('add-book')" :mode="addBookButtonMode"
      >Add a Book</BaseButton
    >
  </BaseCard>
  <FavouriteBooks
    :books="favouriteBooks"
    v-if="selectedTab === 'favourite-books'"
    @delete-book="deleteBook"
  />
  <AddBook v-else @submit-data="addBook" />
</template>

<script>
import FavouriteBooks from './FavouriteBooks.vue';
import AddBook from './AddBook.vue';

export default {
  components: {
    FavouriteBooks,
    AddBook,
  },
  data() {
    return {
      selectedTab: 'favourite-books',
      favouriteBooks: [
        {
          id: 'Skin in the game',
          title: 'Skin in the game',
          author: 'Nassim Nicholas Taleb',
          description:
            'A bold new work that challenges many of our long-held beliefs about risk and reward, politics and religion, finance and personal responsibility.',
          link: 'https://www.amazon.com/Skin-Game-Hidden-Asymmetries-Daily/dp/042528462X',
        },
        {
          id: 'Awareness',
          title: 'Awareness',
          author: 'Anthony de Mello',
          description:
            "Mixing Christian spirituality, Buddhist parables, Hindu breathing exercises, and psychological insight, de Mello's words of hope come together in Awareness in a grand synthesis.",
          link:
            'https://www.amazon.com/Awareness-Opportunities-Reality-Anthony-Mello/dp/0385249373',
        },
      ],
    };
  },
  provide() {
    return {
      deleteBook: this.deleteBook,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addBook(newBook) {
      this.favouriteBooks.unshift(newBook);
      this.selectedTab = 'favourite-books';
    },
    deleteBook(bookId) {
      const bookIndex = this.favouriteBooks.findIndex((book) => book.id === bookId);
      this.favouriteBooks.splice(bookIndex, 1);
    },
  },
  computed: {
    favouriteBooksButtonMode() {
      return this.selectedTab === 'favourite-books' ? null : 'flat';
    },
    addBookButtonMode() {
      return this.selectedTab === 'add-book' ? null : 'flat';
    },
  },
};
</script>

<style>
.header {
  width: 25rem;
  padding: 0.3rem;
  display: flex;
  justify-content: space-around;
}

.header-button {
  font-size: 18px;
}
</style>
