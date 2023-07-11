<template>
  <div class="new-note ">
    <div class="note-title">
      <h2>Title</h2>
      <b-form-input
          v-model="note.title"
          type="text"
          placeholder="Введите заголовок заметки">
      </b-form-input>
    </div>

    <h5 class="pt-20 pb-20">Description</h5>
    <div>
      <b-form-textarea
          id="textarea"
          v-model="note.description"
          placeholder="Введите текст заметки..."
          rows="3"
          max-rows="3"
          no-resize
      ></b-form-textarea>

      <pre class="mt-3 mb-3">{{ note.description}}</pre>
    </div>
    <div>
      <div class="row">
        <div class="col-8 m0-auto d-flex al-center j-around">
          <b-button @click="reset" variant="success" size="sm">Очистить поля</b-button>
          <b-button @click="addNote" variant="success" size="sm">Сохранить заметку</b-button>
        </div>
      </div>

    </div>
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
      },
      reset() {
        this.$emit('reset', this.note)
      }
  }
}
</script>
<style lang="scss">
.form-control {
  margin: 0 auto;
  max-width: 600px;
}
</style>