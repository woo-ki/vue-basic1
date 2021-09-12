<template>
    <div class="black-bg" v-if="detailIsOpened">
        <div class="white-bg">
            <h4>상세페이지</h4>
            <p>상세페이지 내용</p>
            <button @click="detailIsOpened = false">닫기</button>
        </div>
    </div>

    <div class="menu">
        <a href="" v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
    </div>

    <div v-for="(p, i) in products" :key="i">
        <img :src="p.img_path" alt="" class="room-img">
        <h4 @click="detailIsOpened = true">{{ p.name }}</h4>
        <p>{{ p.price }} 만원</p>
        <button @click="reportProc(p)">허위매물신고</button>
        <span> 신고수 : {{ p.report_count }}</span>
    </div>
</template>

<script>

export default {
    name: 'App',
    data() {
        return {
            detailIsOpened: false,
            menus: ['Home', 'Shop', 'About'],
            products: [
                {name: '역삼동원룸', price: 60, report_count: 0, img_path: '/room0.jpg'},
                {name: '천호동원룸', price: 50, report_count: 0, img_path: '/room1.jpg'},
                {name: '마포구원룸', price: 70, report_count: 0, img_path: '/room2.jpg'}
            ],
        }
    },
    methods: {
        reportProc(p) {
            p.report_count++
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
