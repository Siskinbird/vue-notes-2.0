<template>
  <div class="notes d-flex flex-wrap gap10 j-start">
    <div class="note" v-for="(note, index) in notes" :key="index">
      <div class="note-header d-flex al-center j-between">
        <div class="note-header__title d-flex al-center">
          <p class="mt-0 mb-0">{{note.title}}</p>
        </div>
        <div class="note-header__remove">
            <b-icon @click="removeNote(index)" class="removeIco" icon="x-square" font-scale="1"></b-icon>
        </div>
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
  },
  methods: {
    removeNote (index) {
      console.log(`Note id - ${index} removed`);
      this.$emit('remove', index)
    }
  }
}
</script>
<style lang="scss">
.note {
  margin: 20px auto;
  width: 200px;
  text-align: left;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  &-header {
    background-color: #fd7e14;;
    padding: 0;
  }
  p {
    padding: 10px;
    word-wrap: anywhere;
  }
}
.removeIco {
  margin-right: 10px;
  cursor: pointer;
}

</style>