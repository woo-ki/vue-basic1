<template>
    <div class="black-bg" v-if="detailIsOpened">
        <div class="white-bg">
            <h4>{{ products[viewIdx].title }}</h4>
            <p>{{ products[viewIdx].content }}</p>
            <p>{{ products[viewIdx].price }} 원</p>
            <!--            <button @click="detailIsOpened = false">닫기</button>--><!-- props 로 가져온 부모 데이터를 직접적으로 수정할 수 없음.-->
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