<template>
  <Transition name="modal">
    <div class="modal" @click="$emit('closeModal')">
      <div class="modal__block" @click.stop="">
        <h3 class="modal__block-title"> {{ edit ? "O'zgartirish" : "Qo'shish" }} </h3>

        <div class="modal__block-inputs">
          <label>
            <span>Title</span>
            <input v-model="title" type="text" placeholder="Title" />
          </label>
          <label>
            <span>Content</span>
            <input v-model="text" type="text" placeholder="Title" />
          </label>
          <div class="modal__block-btns">
            <button class="modal__btns red" @click="$emit('closeModal')">Bekor qilish</button>

            <button v-if="!edit" class="modal__btns purple" @click="addNote">Qo’shish</button>

            <button v-else class="modal__btns purple" @click="changeNote">O'zgartirish</button>

          </div>
        </div>
      </div>

    </div>
  </Transition>
</template>

<script>

export default {

  props: {
    edit: {
      typeof: Boolean
    },
    editNote: {
      typeof: Object
    }
  },

  data() {
    return {
      title: "",
      text: "",
    }
  },

  methods: {
    changeNote() {
      if (this.title != "" && this.text != "") {
        const newEditNote = {
          id: this.editNote.id,
          title: this.title,
          text: this.text,
          data: new Date().toLocaleDateString()
        }
        this.title = "";
        this.text = "";
        this.$emit("changeNote", newEditNote)
      }
    },

    addNote() {
      if (this.title != "" && this.text != "") {
        const notes = {
          id: new Date().getTime(),
          title: this.title,
          text: this.text,
          data: new Date().toLocaleDateString()
        }
        this.title = "";
        this.text = "";
        this.$emit('addNote', notes)
      }
    }
  }
};
</script>

<style>
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.5s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}
</style>