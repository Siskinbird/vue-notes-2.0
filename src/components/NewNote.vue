<template>
  <div class="new-note ">

<NoteTitle :title="note.title"/>
        <label>Description</label>
        <textarea v-model="note.description"></textarea>
        <b-button @click="reset" variant="success" size="sm">Очистить поля</b-button>
        <b-button @click="addNote" variant="success" size="sm">New note</b-button>
  </div>
</template>

<script>
import NoteTitle from '@/components/partials/NoteTitle.vue'
export default {
  components: {
    NoteTitle
  },
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