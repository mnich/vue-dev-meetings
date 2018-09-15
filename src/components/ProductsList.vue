<template>
    <div id="ProductList">
        <ul class="list">
            <li class="list-item" v-for="p in products" :key="p.id">{{ p.name }}</li>
        </ul>

        <p v-if="!products.length">No products!</p>

        <form @submit.prevent="onSubmit()">
            <input
                    name="product"
                    v-model="newProduct.name"
                    v-validate="'required|min:3'"
            >
            <button>Add</button>
            <!--3- 2. errors are added by default when validation is initialized and have some useful methods -->
            <div v-show="errors.has('product')">
                {{ errors.first('product') }}
            </div>
        </form>
    </div>
</template>

<script>
    import uuid from 'uuid/v4';

    export default {
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
        },
        methods: {
            onSubmit() {
                // 3. On the JS side we need to use yet another injected value called $validator to validate all the fields
                this.$validator.validateAll().then(result => {
                    if (!result) {
                        return;
                    }
                    this.products.push({
                        id: uuid(),
                        ...this.newProduct
                    });
                    this.newProduct.name = '';
                    // 4/ and reset validation state after adding a product
                    this.$validator.reset();
                });
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
