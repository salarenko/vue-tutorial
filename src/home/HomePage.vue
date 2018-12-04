<template>
    <div class="home">
        <div class="">
            <img class="robot" src="../assets/robot-home.png" alt="image of a robot" aria-hidden="true">
        </div>
        <div class="get-started">
            <a href="">Get started!</a>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'HomePage',
        props: {
            msg: String
        }
    }
</script>

<style scoped>
    .home {
        text-align: center;
    }
</style>
