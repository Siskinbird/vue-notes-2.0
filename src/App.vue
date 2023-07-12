<template>
  <div id="app">
    <div class="container-sm">
      <div class="row-md">
        <div class='col-9 m0-auto'>
          <h1>{{ title }}</h1>

          <Message v-if="message" :message="message" :showDismiss="showDismiss"/>
        </div>


        <div class='col-9 m0-auto'>
          <!--new note-->

          <NewNote
              :note="note"
              @addNote="addNote"
              @reset="reset"
          />
        </div>


          <div class='col-9 m0-auto'>
            <div class="note-header d-flex j-end al-center mt-20">
              <b-icon icon="grid" class="cube mr-15 pointer" :class="{ active:grid }" @click="grid = true"></b-icon>
              <b-icon icon="view-stacked" class="horizon pointer" :class="{ active:!grid }" @click="grid = false"></b-icon>
            </div>


          <!--notes-->
          <Notes
              :notes="notes"
              :grid="grid"
              @remove="removeNote"
          />

        </div>


      </div>





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
      grid: true,
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

      if (title === '') {
        this.message = 'Заголовок заметки не может быть пустым!'
        this.showDismiss = true
        return false;
      } else if (description === '') {
        this.message = 'Заголовок заметки не может быть пустым!'
        this.showDismiss = true
        return false;
      } else {
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
      this.note.title = ''
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
  font-family: Monospaced, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.note-header {
  margin-top: 30px;
}

.d-flex {
  display: flex;
}

.flex-column {
  flex-direction: column;
}
.j-end {
  justify-content: end;
}
.flex-wrap {
  flex-wrap: wrap;
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
.mr-15 {
  margin-right: 6px;
}
.pointer {
  cursor: pointer;
}
.bi-grid, .horizon, .cube {
  transition: ease-in-out .3s;
  &:hover {
    transform: scale(1.3);
  }

  &.active{
    color: #28a745;
    box-shadow: 4px 4px 8px 0 rgba(40, 167, 69, 0.2);
    transform: scale(1.3);
  }
}
</style>
