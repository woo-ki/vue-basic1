<template>
    <div>
        <h4>{{ products[0].name }}</h4>
        <p>{{ products[0].price }} 만원</p>
    </div>
    <div>
        <h4>{{ products[1].name }}</h4>
        <p>{{ products[1].price }} 만원</p>
    </div>
    <div>
        <h4>{{ products[2].name }}</h4>
        <p>{{ products[2].price }} 만원</p>
    </div>
</template>

<script>

export default {
    name: 'App',
    data() {
        return {
            products: [
                {name: '역삼동원룸', price: 60},
                {name: '천호동원룸', price: 50},
                {name: '마포구원룸', price: 70}
            ],
        }
    },
    components: {}
}
</script>

<style>

</style>
