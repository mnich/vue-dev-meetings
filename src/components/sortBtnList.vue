<template>
    <div>
        <button @click="sort" class="btn btn-sm btn-block btn-default" type="button">Sort list</button>
    </div>
</template>

<script>
    export default {
        name: 'SortBtnList',
        props: {
            products: Array
        },
        methods: {
            sort(){
                this.$emit('sortItems');
            }
        },
    };
</script>
<style scoped>

</style>
