<template>

    <transition name="fade">
        <DetailModal @closeDetail="closeDetail()" :products="products" :detailIsOpened="detailIsOpened"
                     :viewIdx="viewIdx"/>
    </transition>

    <div class="menu">
        <a href="" v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
    </div>

    <Discount/>

    <OneRoom @openDetail="openDetail($event)" v-for="(p, i) in products" :key="i" :p="p"/>

</template>

<script>

import products from './assets/js/oneroom.js';
import Discount from "@/components/Discount";
import DetailModal from "@/components/DetailModal";
import OneRoom from "@/components/OneRoom";

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
        },
        closeDetail() {
            this.detailIsOpened = false;
        }
    },
    components: {
        OneRoom,
        DetailModal,
        Discount
    }
}
</script>

<style>
.fade-enter-from, .fade-leave-to {
    opacity: 0;
}

.fade-enter-active, .fade-leave-active {
    transition: all 1s;
}

.fade-enter-to, .fade-leave-from {
    opacity: 1;
}

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

body {
    margin: 0;
}

div {
    box-sizing: border-box;
}
</style>
