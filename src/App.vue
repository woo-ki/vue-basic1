<template>
    <div class="black-bg" v-if="detailIsOpened">
        <div class="white-bg">
            <h4>{{ products[viewIdx].title }}</h4>
            <p>{{ products[viewIdx].content }}</p>
            <p>{{ products[viewIdx].price }} 원</p>
            <button @click="detailIsOpened = false">닫기</button>
        </div>
    </div>

    <div class="menu">
        <a href="" v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
    </div>

    <div v-for="(p, i) in products" :key="i">
        <img :src="p.image" class="room-img" alt="">
        <h4 @click="openDetail(i)">{{ p.title }}</h4>
        <p>{{ p.price }}원</p>
    </div>
</template>

<script>

import products from './assets/js/oneroom.js';

export default {
    name: 'App',
    data() {
        return {
            detailIsOpened: false,
            menus: ['Home', 'Shop', 'About'],
            products: products,
            viewIdx: 0
        }
    },
    methods: {
        openDetail(i) {
            this.detailIsOpened = true;
            this.viewIdx = i;
        }
    },
    components: {}
}
</script>

<style>
.menu {
    background: darkslateblue;
    padding: 15px;
    border-radius: 5px;
}

.menu a {
    color: white;
    padding: 10px;
    text-decoration: none;
}

.room-img {
    width: 100%;
    margin-top: 40px;
}

body {
    margin: 0;
}

div {
    box-sizing: border-box;
}

.black-bg {
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    position: fixed;
    padding: 20px;
}

.white-bg {
    width: 100%;
    background: white;
    border-radius: 8px;
    padding: 20px;
}
</style>
