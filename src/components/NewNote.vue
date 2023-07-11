<template>
  <div class="new-note ">
    <div class="note-title">
      <h5 class="title">Title:</h5>
      <b-form-input
          class="m0-auto"
          v-model="note.title"
          type="text"
          placeholder="Введите заголовок заметки">
      </b-form-input>
    </div>
  <br/>
    <h5 class="description">Description:</h5>
    <div>
      <b-form-textarea
          class="m0-auto"
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
        <div class="col-12 m0-auto d-flex al-center j-between">
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
  //margin-top: 20px;
}
.description, .title {
  //margin-top: 10px;
  //margin-bottom: 10px;
  text-align: left;
  font-weight: 600;
  font-size: 16px;
}
h5 {

}

</style>