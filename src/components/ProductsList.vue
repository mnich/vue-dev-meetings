<template>
    <div id="ProductList">
        <ul class="list">
            <li class="list-item" v-for="p in products" :key="p.id">{{ p.name }}</li>
        </ul>

        <add-product-form v-bind:products="products"></add-product-form>

        <p v-if="!products.length">No products!</p>

    </div>
</template>

<script>
    import AddProductForm from "./productAddForm.vue";

    export default {
        components: {AddProductForm},
        name: 'ProductList',
        data() {
            return {
                products: [{
                    id: 0,
                    name: 'Coffee'
                }, {
                    id: 1,
                    name: 'Pizza'
                }],
                newProduct: {
                    name: ''
                }
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
