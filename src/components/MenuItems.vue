<template>
    <div>
        <div>
            <input type="number" ref="user_number">
            <button @click="filter_prices">Price Filter</button>
        </div>
        <section class="menu_container">
            <div v-for="(item,i) in items" :key="i">
                <span v-if="item.price <= max_price">
                    <h3>{{ item.title }}</h3>
                    <p>{{ item.description }}</p>
                    <img :src="item.image_url" :alt="item.description">
                    <h6>{{ item.price }}</h6>
                </span>
            </div>
        </section>
    </div>
</template>

<script>
    export default {
        methods: {
            filter_prices: function() {
                let input_tag = this.$refs[`user_number`];
                let input_value = input_tag[`value`];
                this.max_price = input_value;
            }
        },
        data() {
            return {
                max_price: 1000,
                items: [
                    {
                        title: `Pizza`,
                        price: 13.50,
                        image_url: `/images/pizza.jpg`,
                        description: `It is a great pizza.`
                    },
                    {
                        title: `Pasta`,
                        price: 15.50,
                        image_url: `/images/pasta.jpg`,
                        description: `It is a great pasta.`
                    },
                    {
                        title: `Calzone`,
                        price: 11.50,
                        image_url: `/images/calzone.jpg`,
                        description: `It is a great calzone.`
                    },
                    {
                        title: `Salad`,
                        price: 9.00,
                        image_url: `/images/salad.jpg`,
                        description: `It is a great salad.`
                    },
                ]
            }
        },
    }
</script>

<style scoped>
img {
    max-width: 100%;
}

.menu_container {
    display: grid;
    place-items: center;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 30px;
}

</style>