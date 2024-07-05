<template>
  <header class="header">
    <nav class="nav" v-if="header">
      <button class="nav__lang">RU</button>
      <h3 class="nav__title">Eslatmalar</h3>
      <button class="nav__search" @click="navOpen">
        <img src="@/assets/images/search.svg" alt="" />
      </button>
    </nav>

    <nav class="nav" v-else>
      <div class="nav__opt">
        <button class="nav__lang" @click="navOpen">
          <img src="@/assets/images/arrow.svg" alt="" />
        </button>
        <input v-model="search" type="text" class="nav__inp" placeholder="Qidirish..." />
      </div>
      <button class="nav__search" @click="dellValue">
        <img src="@/assets/images/close.svg" alt="" />
      </button>
    </nav>

  </header>
</template>

<script>
export default {

  props: {
    massiv: {
      typeof: Array
    }
  },

  data() {
    return {
      header: true,
      search: "",
    };
  },

  methods: {
    navOpen() {
      this.header = !this.header
    },
    dellValue() {
      this.search = ""
    }
  },
  
  watch: {
    search(newValue) {
    //  console.log(newValue);
    
     this.$emit('setSearch', newValue)
    }
  }



};
</script>

<style></style>