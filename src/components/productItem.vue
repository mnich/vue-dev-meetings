<template>
    <li class="list-item">
        {{ name }}
        <button class="btn btn-danger" v-on:click="removeItem(id)">Remove</button>
    </li>
</template>

<script>
    export default {
        name: 'ProductItem',
        props: {
            name: String,
            id: String
        },
        methods: {
            removeItem(key) {
                this.$emit('removeItem', key);
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
