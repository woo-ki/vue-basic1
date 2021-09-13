<template>

    <transition name="fade">
        <DetailModal @closeDetail="closeDetail()" :products="products" :detailIsOpened="detailIsOpened"
                     :viewIdx="viewIdx"/>
    </transition>

    <div class="menu">
        <a href="" v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
    </div>

    <Discount/>

    <select id="filter" v-model="filterIdx">
        <option value="0">가격 오름차순</option>
        <option value="1">가격 내림차순</option>
        <option value="2">가나다 오름차순</option>
        <option value="3">가나다 내림차순</option>
    </select>&nbsp;
    <button @click="basicSort()">정렬</button>
    <br>
    <input type="range" max="50" v-model="range"/>
    <button @click="removeOverFifty()">{{ range }}만원 이상 삭제</button>
    <br>
    <button @click="revertSort()">되돌리기</button>

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
            productsOrigin: [...products],
            detailIsOpened: false,
            menus: ['Home', 'Shop', 'About'],
            products: products,
            viewIdx: 0,
            filterIdx: 0,
            range: 0,
        }
    },
    methods: {
        openDetail(i) {
            this.detailIsOpened = true;
            this.viewIdx = i;
        },
        closeDetail() {
            this.detailIsOpened = false;
        },
        basicSort() {
            let t = Number(this.filterIdx);
            if (t === 0 || t === 1) {
                this.products.sort(function (a, b) {
                    return a.price - b.price
                });
                if (t === 1) {
                    this.products.reverse();
                }
            } else {
                this.products.sort(function (a, b) {
                    let nameA = a.title.toUpperCase(); // ignore upper and lowercase
                    let nameB = b.title.toUpperCase(); // ignore upper and lowercase
                    if (nameA < nameB) {
                        return -1;
                    }
                    if (nameA > nameB) {
                        return 1;
                    }
                    // 이름이 같을 경우
                    return 0;
                });
                if (t === 3) {
                    this.products.reverse();
                }
            }
        },
        removeOverFifty() {
            this.products = [...this.productsOrigin];

            let r = this.range * 10000;
            this.products = this.products.filter(function (item) {
                return item.price < r
            })
        },
        revertSort() {
            this.products = [...this.productsOrigin];
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
    margin: 0 auto;
    width: 100%;
}

div {
    box-sizing: border-box;
}

html * {
    max-width: 540px;
}
</style>
