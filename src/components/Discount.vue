<template>
    <div class="discount" v-if="discountIsVisible">
        <h4>지금 결제하면 {{discountRate}}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: "Discount",
    props: {
        discountIsVisible: Boolean,
        discountRate: Number
    },
    mounted() {
        this.$emit('decreaseDiscount');
    }
}
</script>

<style scoped>
.discount {
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
</style>