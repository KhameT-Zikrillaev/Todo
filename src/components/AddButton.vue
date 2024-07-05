<template>
  <button class="addBtn" @click="$emit('openModal')">
    <img src="@/assets/images/pencil.svg" alt="" />
  </button>
</template>

<script>
export default {

};
</script>

<style scoped>
.addBtn {
  box-shadow: 0px 1px 3px 0px rgba(0, 0, 0, 0.30), 0px 4px 8px 3px rgba(0, 0, 0, 0.15);
  width: 56px;
  height: 56px;
  /* background: #F3EDF7; */
  background: v-bind(bg);
  cursor: pointer;
  border: none;
  border-radius: 16px;
  position: fixed;
  right: 30px;
  bottom: 30px;
}

</style>