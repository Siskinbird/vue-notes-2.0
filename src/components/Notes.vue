<template>
  <div class="notes">
    <div class="note" v-for="(note, index) in notes" :key="index">
      <div class="note-header">
        <p>{{note.title}}</p>
      </div>
      <div class="note-body">
        <p>{{note.description}}</p>
        <p>{{note.date}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    notes: {
      type: Array,
      required: true
    }
  }
}
</script>