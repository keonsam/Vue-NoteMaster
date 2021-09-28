<template>
  <div id="app">
    <NoteForm
      :title.sync="title"
      :description.sync="description"
      @submit="onSubmit"
    />
    <NoteList :notes="notes" @delete="onDelete" />
  </div>
</template>

<script>
import NoteForm from "./components/NoteForm.vue";
import NoteList from "./components/NoteList.vue";

export default {
  name: "App",
  components: {
    NoteForm,
    NoteList,
  },
  data() {
    return {
      title: "",
      description: "",
      notes: [],
    };
  },
  mounted() {
    if (localStorage.notes) this.notes = JSON.parse(localStorage.notes);
  },
  methods: {
    onSubmit() {
      let note = {
        id: "id" + new Date().getTime(),
        title: this.title,
        description: this.description,
        date: Date(),
      };
      const newNotes = [...this.notes, note];
      localStorage.notes = JSON.stringify(newNotes);
      this.notes = newNotes;
      this.title = "";
      this.description = "";
    },
    onDelete(id) {
      const newNotes = this.notes.filter((x) => x.id !== id);
      localStorage.notes = JSON.stringify(newNotes);
      this.notes = newNotes;
    },
  },
};
</script>

<style>
*,
*:before,
*:after {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 1024px;
  margin: 0 auto;
  padding: 30px 15px;
}
</style>
