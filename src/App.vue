<template>
    <div id="app">
        <Header msg="Dev Meetings - vue app sample "/>
        <product-list></product-list>
    </div>
</template>

<script>
    import Header from './components/header.vue';
    import ProductList from './components/ProductsList.vue';

    export default {
        name: 'app',
        components: {
            Header,
            ProductList
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        max-width: 1200px;
        width: 100%;
        margin: 0 auto;
    }
</style>
