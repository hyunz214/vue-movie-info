<template>
    <h1>영화 정보</h1>

    <div v-for="(movie, i) in data" :key="i">
        <h3 class="bg-yellow">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <button @:click="increaseLike(i)">좋아요</button>
        <span>{{ movie.like }}</span>
    </div>
</template>

<script>
export default {
    name: "App",
    data() {
        return {
            data: [
                { title: "노량", year: 2023, category: "액션, 드라마", like: 0 },
                { title: "아쿠아맨", year: 2023, category: "액션, 판타지, 어드벤처", like: 0 },
            ],
        };
    },
    methods: {
        increaseLike(i) {
            this.data[i].like += 1;
        },
    },
};
</script>

<style>
.bg-yellow {
    background: gold;
    padding: 10px;
}
</style>
