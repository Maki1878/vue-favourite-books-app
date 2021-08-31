<template>
  <li>
    <BaseCard>
      <header>
        <h3>{{ title }}</h3>

        <BaseButton mode="flat" @click="deleteBook(id)">Delete</BaseButton>
      </header>
      <h4>{{ author }}</h4>
      <p>{{ description }}</p>
      <nav>
        <a target="_blank" :href="link">Buy the book on Amazon</a>
      </nav>
    </BaseCard>
  </li>
</template>

<script>
export default {
  props: ['title', 'author', 'description', 'link', 'id'],
  inject: ['deleteBook'],
};
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #2215f2;
}

a:hover,
a:active {
  color: #473ed9;
}
</style>
