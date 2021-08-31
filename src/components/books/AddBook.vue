<template>
  <BaseDialog v-if="inputIsInvalid" @close="closeDialog">
    <template #header>
      <h2>Input is not Valid</h2>
    </template>
    <template #default>
      <p>
        At least one input value is not valid. Please check all input fields and enter the correct
        values.
      </p>
    </template>
    <template #close>
      <BaseButton @click="closeDialog">Okay</BaseButton>
    </template>
  </BaseDialog>
  <BaseCard>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" v-model.trim="titleInput" />
      </div>
      <div class="form-control">
        <label for="author">Author</label>
        <input id="author" name="author" type="text" v-model.trim="authorInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea name="description" id="description" rows="3" v-model.trim="descInput"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" v-model.trim="linkInput" />
      </div>
      <div>
        <BaseButton type="submit">Add Book</BaseButton>
      </div>
    </form>
  </BaseCard>
</template>

<script>
export default {
  emits: ['submit-data'],
  data() {
    return {
      titleInput: '',
      authorInput: '',
      descInput: '',
      linkInput: '',
      inputIsInvalid: false,
    };
  },

  methods: {
    submitData() {
      const bookTitle = this.titleInput;
      const bookAuthor = this.authorInput;
      const bookDescription = this.descInput;
      const bookLink = this.linkInput;

      if (bookTitle === '' || bookAuthor === '' || bookDescription === '' || bookLink === '') {
        this.inputIsInvalid = true;
        return;
      }
      const newBook = {
        id: new Date().toISOString(),
        title: bookTitle,
        author: bookAuthor,
        description: bookDescription,
        link: bookLink,
      };

      this.$emit('submit-data', newBook);
    },
    closeDialog() {
      this.inputIsInvalid = false;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 8px;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
