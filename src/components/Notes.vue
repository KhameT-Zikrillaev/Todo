<template>
  <div class="note">
    <div class="container">
      <h2 class="note__title">Barcha eslatmalar</h2>
      <button class="note__btn" @click="changeNotes">
        <img src="@/assets/images/grid.svg" alt="" v-if="grid" />
        <img src="@/assets/images/flex.svg" alt="" v-else />
        <span>{{ grid ? "Roʻyxat" : "Setka" }}</span>
      </button>
    </div>
    <div class="note__list container" :class="{ 'active': !grid }">

      <NoteItem v-for="note in notes" :note="note" @dellNote="$emit('delNote', note.id)" :key="note.id"
        @change="$emit('change', note.id)" />
    </div>
  </div>
</template>

<script>
import NoteItem from './NoteItem.vue';

export default {

  components: {
    NoteItem
  },

  props: {
    notes: {
      typeof: Array,
    }
  },

  data() {
    return {
      grid: true,
    };
  },

  methods: {
    changeNotes() {
      this.grid = !this.grid;
    },
  },
};
</script>

<style></style>