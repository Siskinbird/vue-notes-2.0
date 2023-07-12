<template>
  <div class="notes d-flex flex-wrap gap10 j-between">
    <div class="note" :class="{full: !grid}" v-for="(note, index) in notes" :key="index">
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
    },
    grid: {
      type: Boolean,
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
<style lang="scss" scoped>

.notes {
  margin-top: 30px;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
}
.note {
  margin: 20px auto;
  width: 45%;
  gap: 10px;
  text-align: left;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  transition: ease-in-out .4s;
  &-header {
    background-color: #fd7e14;;
    padding: 0;
    margin: 0;
  }
  &.full {
    width: 96%
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