<template>
  <div class="new-note">
    <label>Title</label>
    <input v-model="note.title" type="text">
    <label>Description</label>
    <textarea v-model="note.description"></textarea>
    <b-button @click="reset" variant="success">Очистить поля</b-button>
    <b-button @click="addNote" variant="success">New note</b-button>
  </div>
</template>

<script>
export default {
    props: {
      note: {
        type: Object,
        required: true
      }
    },
  methods: {
      addNote() {
        this.$emit('addNote', this.note)
      }
  }
}
</script>