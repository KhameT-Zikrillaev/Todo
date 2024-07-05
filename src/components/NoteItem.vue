<template>
    <div class="note__list-item">
        <h3 class="note__list-title">{{ note.title }}</h3>
        <p class="note__list-data">{{ note.data }}</p>
        <p class="note__list-desc">
            {{ note.text }}
        </p>
        <div class="note__list-btn">
            <button class="note__btns" @click="$emit('change', note.id)">
                <img src="@/assets/images/pencil.svg" alt="" />
                <span>O'ZGARTIRISH</span>
            </button>
            <button class="note__btns" @click="$emit('dellNote', note.id)">
                <img src="@/assets/images/cart.svg" alt="" />
                <span>o'chirish</span>
            </button>
        </div>
    </div>
</template>

<script>
export default {

    props: {
        note: {
            typeof: Array
        }
    },

}
</script>

<style></style>