<template>
    <Navbar />
    <Event :text="text" />
    <p>
        <button @click="showAllMovie">전체보기</button>
    </p>
    <SearchBar :data="data_temp" @searchMovie="searchMovie($event)" />
    <Movies :data="data_temp" @increaseLike="increaseLike" @openModal="openModal" />
    <Modal :isModal="isModal" :data="data_temp" :selectedMovieIndex="selectedMovieIndex" @closeModal="isModal = false" />
</template>

<script>
import data from "./assets/datas/movies";
import Navbar from "./components/Navbar.vue";
import Event from "./components/Event.vue";
import Modal from "./components/Modal.vue";
import Movies from "./components/Movies.vue";
import SearchBar from "./components/SearchBar.vue";

export default {
    name: "App",
    data() {
        return {
            isModal: false,
            data: data, //원본
            data_temp: [...data], //사본
            selectedMovieIndex: 0,
            text: "NETPLIX 강렬한 운명의 드라마, 경성크리처",
        };
    },
    components: {
        Navbar: Navbar,
        Event: Event,
        Modal: Modal,
        Movies: Movies,
        SearchBar: SearchBar,
    },
    methods: {
        increaseLike(id) {
            this.data.find((movie) => {
                if (movie.id === id) {
                    movie.like += 1;
                }
            });
        },
        openModal(i) {
            this.selectedMovieIndex = i;
            this.isModal = true;
        },
        searchMovie(title) {
            this.data_temp = this.data.filter((movie) => {
                return movie.title.includes(title);
            });
        },
        showAllMovie() {
            this.data_temp = [...this.data];
        },
    },
};
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
}

body {
    max-width: 768px;
    margin: 0 auto;
    padding: 20px;
}

h1,
h2,
h3 {
    margin-bottom: 1rem;
}

p {
    margin-bottom: 0.5rem;
}

button {
    margin-right: 10px;
    margin-top: 1rem;
}

.item {
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;
}

.item figure {
    width: 30%;
    margin-right: 1rem;
}

.item img {
    width: 100%;
}

.item .info {
    width: 100%;
}

.modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
}
</style>
