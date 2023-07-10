<template>
  <div id="app">
    <div class="container">
      <h1>{{ title }}</h1>

      <Message v-if="message" :message="message" :showDismiss="showDismiss"/>

      <NewNote
          :note="note"
          @addNote="addNote"
      />
      <!--      <div class="message" v-if="message">-->
      <!--        <p>{{message}}</p>-->
      <!--      </div>-->


      <!--new note-->

      <!--notes-->
      <Notes
          :notes="notes"
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

      if (title === '' && description === '') {
        this.message = 'Title or description can`t be blank'
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
</style>
