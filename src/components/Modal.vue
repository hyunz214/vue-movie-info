<template>
    <div class="modal" v-if="isModal">
        <div class="inner">
            <div>
                <h3>{{ data[selectedMovieIndex].title }}</h3>
                <p>장르: {{ data[selectedMovieIndex].category }}</p>
                <span>좋아요: {{ data[selectedMovieIndex].like }}</span>
            </div>
            <button @:click="$emit('closeModal')">닫기</button>
        </div>
    </div>
</template>
<script>
export default {
    name: "ModalComponent",
    props: {
        isModal: Boolean,
        selectedMovieIndex: Number,
        data: Array,
    },
};
</script>
<style></style>
