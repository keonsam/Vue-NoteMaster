<template>
  <ul class="list">
    <li class="list-item" v-for="note in notes" :key="note.id">
      <header class="header">
        <h3 class="title" role="title">{{ note.title }}</h3>
        <span class="close" role="close" @click="$emit('delete', note.id)"
          >x</span
        >
      </header>
      <section>
        <p>Created On: {{ note.date }}</p>
        <p>{{ note.description }}</p>
      </section>
    </li>
  </ul>
</template>

<script>
export default {
  name: "NoteList",
  props: {
    notes: {
      type: [Object],
      required: true,
    },
  },
};
</script>

<style scoped>
.list {
  display: flex;
  gap: 10px;
  list-style: none;
}
.list-item {
  border: 1px solid black;
  padding: 10px;
  border-radius: 4px;
}

.header {
  display: flex;
  justify-content: space-between;
}

.title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 16px;
}

.close {
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
}
</style>
