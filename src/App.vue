<template>
    <div class="menu">
        <a href="" v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
    </div>
    <div v-for="(p, i) in products" :key="i">
        <h4>{{ p.name }}</h4>
        <p>{{ p.price }} 만원</p>
    </div>
</template>

<script>

export default {
    name: 'App',
    data() {
        return {
            menus: ['Home', 'Shop', 'About'],
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
</style>
