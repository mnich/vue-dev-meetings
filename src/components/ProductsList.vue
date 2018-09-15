<template>
    <div id="ProductList">
        <transition-group class="list-group-item" tag="ul">
            <productItem v-for="p in products" :name="p.name" :id="p.id" :key="p.id"
                @removeItem="removeItem"></productItem>
        </transition-group>
        <add-product-form :products="products"></add-product-form>

        <SortBtnList @sortItems="sort"></SortBtnList>

        <p v-if="!products.length">No products!</p>
    </div>
</template>

<script>
    import AddProductForm from "./productAddForm.vue";
    import ProductItem from "./productItem.vue";
    import SortBtnList  from "./sortBtnList.vue";



    export default {


        components: {AddProductForm, ProductItem, SortBtnList},
        name: 'ProductList',
        data() {
            return {
                products: [{
                    id: '0',
                    name: 'Coffee'
                }, {
                    id: '1',
                    name: 'Pizza'
                }]
            }
        },
        methods: {
            removeItem(key) {
                this.products.splice(key, 1);
            },
            sort() {
                this.products.sort((a, b) => {
                    if (a.name.toLowerCase() < b.name.toLowerCase() ) return -1;
                    if (a.name.toLowerCase() > b.name.toLowerCase() ) return 1;
                    return 0;
                });
            }
        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .list-item {
        display: flex;
        align-items: center;
        justify-content: space-between;
        transition: all 0.5s;
        margin-bottom: 10px;
    }

    .v-enter,
    .v-leave-to
        /* .card-leave-active for <2.1.8 */ {
        opacity: 0;
        transform: scale(0);
    }

    .v-enter-to {
        opacity: 1;
        transform: scale(1);
    }

    .v-leave-active {
        /*position: absolute;*/
    }

    .v-move {
        opacity: 1;
        transition: all 0.5s;
    }
</style>
