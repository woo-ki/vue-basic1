<template>
    <div class="black-bg" v-if="detailIsOpened">
        <div class="white-bg">
            <img class="w100p" :src="products[viewIdx].image" alt="">
            <h4>{{ products[viewIdx].title }}</h4>
            <p>{{ products[viewIdx].content }}</p>
            <p>{{ products[viewIdx].price }} 원</p>
            <button @click="$emit('closeDetail')">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "DetailModal",
    props: {
        products: Array,
        detailIsOpened: Boolean,
        viewIdx: Number
    }
}
</script>

<style scoped>
.w100p {
    width: 100%;
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