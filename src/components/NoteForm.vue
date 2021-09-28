<template>
  <form class="form" @submit.prevent="$emit('submit')">
    <label for="title" class="label">
      Title:
      <input
        id="Enter title"
        class="input"
        placeholder="title"
        :value="title"
        @input="$emit('update:title', $event.target.value)"
      />
    </label>
    <label for="description" class="label">
      Description
      <textarea
        id="description"
        class="textarea"
        placeholder="Enter description"
        :value="description"
        @input="$emit('update:description', $event.target.value)"
      ></textarea>
    </label>
    <button class="button" type="submit">Save</button>
  </form>
</template>

<script>
export default {
  name: "NoteForm",
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px 0;
}

.label {
  text-align: start;
  width: 100%;
  max-width: 750px;
}

.input {
  display: block;
  font-size: 14px;
  padding: 7px 15px;
  margin-top: 6px;
  width: 100%;
  border-radius: 4px;
}

.textarea {
  display: block;
  width: 100%;
  font-size: 14px;
  padding: 7px 15px;
  margin-top: 6px;
  max-width: 750px;
  border-radius: 4px;
}

.button {
  background: blue;
  padding: 15px;
  border: none;
  outline: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
