<template>
    <div>
        <img :src="p.image" class="room-img" alt="">
        <h4>{{ p.title }}</h4>
        <p>{{ p.price }}원</p>
    </div>
</template>

<script>
export default {
    name: "OneRoom",
    props: {
        p: Object,
    }
}
</script>

<style scoped>
.room-img {
    width: 100%;
    margin-top: 40px;
}
</style>