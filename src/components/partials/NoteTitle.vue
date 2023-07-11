<template>
  <div class="note-title">
    <label>Title</label>
    <input v-model="title" type="text">
  </div>
</template>

<script>

export default {
  props: {
    title: {
      type: String,
      require: true
    }
  },
  data() {
    return {
      title: this.title
    }
  }
}
</script>