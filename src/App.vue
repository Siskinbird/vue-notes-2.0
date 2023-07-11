<template>
  <div id="app">
    <div class="container-sm">
      <h1>{{ title }}</h1>

      <Message v-if="message" :message="message" :showDismiss="showDismiss"/>

      <!--new note-->

      <NewNote
          :note="note"
          @addNote="addNote"
          @reset="reset"
      />

      <!--notes-->
      <Notes
          :notes="notes"
          @remove="removeNote"
      />

    </div>
  </div>
</template>

<script>
import Message from '@/components/Message.vue'
import NewNote from '@/components/NewNote.vue'
import Notes from '@/components/Notes.vue'


export default {
  components: {
    Message,
    NewNote,
    Notes
  },
  name: 'App',
  data() {
    return {
      title: 'Notes App',
      message: null,
      showDismiss: false,
      note: {
        title: '',
        description: ''
      },
      notes: [
        {
          title: 'First note',
          description: 'Description for first note',
          date: new Date(Date.now()).toLocaleDateString()
        },
        {
          title: 'Second note',
          description: 'Description for Second note',
          date: new Date(Date.now()).toLocaleDateString()
        },
        {
          title: 'Third note',
          description: 'Description for Third note',
          date: new Date(Date.now()).toLocaleDateString()
        }
      ]
    }
  },
  methods: {
    addNote() {
      // console.log(this.note)

      let { title, description} = this.note

      if (title === '' || description === '') {
        this.message = 'Заголовок заметки не может быть пустым!'
        this.showDismiss = true
        return false;
      }
      else {
        this.notes.push({
          title,
          description,
          date: new Date(Date.now()).toLocaleDateString()
        })
        this.reset()
        this.message = null
        this.showDismiss = false
      }
    },
    reset() {
      this.note.title = '',
      this.note.description = ''
    },
    removeNote(index) {
      this.notes.splice(index, 1)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.d-flex {
  display: flex;
}

.flex-column {
  flex-direction: column;
}

.flex-wrap {
  flex-wrap: wrap;
}

.flex-1-1-auto {
  flex: 1 1 auto;
}

.flex-50 {
  flex: 50%;
}

.flex-33 {
  flex: 33%;
}

.al-center {
  align-items: center;
}

.al-start {
  align-items: flex-start;
}

.al-end {
  align-items: flex-end;
}

.j-between {
  justify-content: space-between;
}

.j-around {
  justify-content: space-around;
}

.j-center {
  justify-content: center;
}

.gap-20 {
  gap: 20px;
}

.gap-15 {
  gap: 15px;
}

.gap-10 {
  gap: 10px;
}

.p-10 {
  padding: 10px;
}

.m0-auto {
  margin: 0 auto;
}
//TODO Сделать сетку для блокнота
</style>
