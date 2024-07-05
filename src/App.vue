<template>
  <Header :massiv="massiv" @setSearch="searchValue = $event" />
  <Notes :notes="filterNotes" @delNote="delNote" @change="change" />
  <AddButton @openModal="openModal"   />
  <Modal v-show="modalOpen" @closeModal="closeModal" @addNote="addNote" :edit="edit" :editNote="editNote"
    @changeNote="changeNote" />
    <p v-for="item in arr" :key="item.name">
      {{ item.name }}
      <img :src="item.icon" alt="">
    </p>
</template>

<script>

import Header from "@/components/Header.vue";
import Notes from "@/components/Notes.vue";
import AddButton from "./components/AddButton.vue";
import Modal from "./components/Modal.vue";

export default {
  components: {
    Header,
    Notes,
    AddButton,
    Modal,
  },
  data() {
    return {
      massiv: ['asdjaksdjkalsd'],
      modalOpen: false,
      notes: [],
    
      searchValue: "",
      edit: false,
      editNote: null,
      h1: "hello"
    }
  },

  computed: {
    filterNotes() {
      return this.notes.filter((note) => note.title.toLowerCase().includes(this.searchValue.toLowerCase()))
    },
    toUpper() {
      return this.h1.toUpperCase()
    }
  },

  methods: {
    delNote(id) {
      console.log(id);
      //  console.log('salom');

      let index = this.notes.findIndex((item) => {
        return item.id == id;
      })

      this.notes.splice(index, 1)
    },
    changeNote(newNote) {
      // console.log(this.notes);
      console.log(newNote);
      this.notes.forEach((note) => {
        if (note.id == newNote.id) {
          note.title = newNote.title
          note.text = newNote.text;
          note.data = newNote.data
        }
      })

      this.closeModal()

    },

    change(id) {
      // console.log(id);
      this.modalOpen = this.edit = true
      let currentNote = this.notes.find((note) => note.id == id)

      this.editNote = currentNote
    },

    addNote(note) {
      console.log(note);
      this.notes.push(note)
      this.closeModal()
    },

    openModal() {
      this.modalOpen = true;
      this.edit = false
    },
    closeModal() {
      this.modalOpen = false;
    },
    getNotes() {
      let localNotes = localStorage.notes;
      if (localNotes) {
        this.notes = JSON.parse(localNotes)
      }
    }

  },

  watch: {
    notes: {
      handler() {
        localStorage.notes = JSON.stringify(this.notes)
      },
      deep: true
    }
  },
  created() {

  },
  mounted() {
    this.getNotes()
  }
};


</script>

<style></style>