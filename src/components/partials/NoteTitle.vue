<template>
  <div class="note-title">
    <label>Title</label>
    <input v-model="note.title" type="text">
  </div>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      require: true
    },
    note: {
      type: Object,
      require: true
    }
  }
}
</script>