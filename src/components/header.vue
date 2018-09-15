<template>
    <div class="header">
        <a href="/">
            <img class="header-logo" src="../assets/devmeetings.png" alt="" />
        </a>
        <h1 class="header-title">{{ msg }}</h1>
    </div>
</template>

<script>
    export default {
        name: 'Header',
        props: {
            msg: String
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .header {
        display: flex;
        align-items: center;
        margin: 20px;
    }

   .header-title {
       line-height: 2;
   }

    .header-logo {
        margin-right: 10px;
    }
</style>
