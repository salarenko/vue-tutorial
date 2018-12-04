<template>
    <div id="app">
        <header>
            <nav>
                <ul>
                    <li class="nav-item">
                        <img class="logo" src="./assets/build-a-bot-logo.png" alt="Logo - robot head">
                        Create a bot!
                    </li>
                </ul>
            </nav>
        </header>
        <main>
            <RobotBuilder/>
            <!--<HomePage msg="Welcome to Your Vue.js App"/>-->
        </main>
    </div>
</template>

<script>
    // import HomePage from './home/HomePage.vue'
    import RobotBuilder from './build/RobotBuilder'

    export default {
        name: 'app',
        components: {
            // HomePage,
            RobotBuilder
        }
    }
</script>

<style>

    header {
        background-color: #999;
        margin: 0 auto;
    }

    ul {
        padding: 3px;
        display: flex;
    }

    .nav-item {
        display: inline-block;
        padding: 5px 10px;
        font-size: 22px;
        border-right: 1px solid #bbb;
    }

    .logo {
        vertical-align: middle;
        height: 30px;
    }

    body {
        background: linear-gradient(to bottom, #555, #999);
        background-attachment: fixed;
    }

    #app {
        font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    }

    main {
        margin: 0 auto;
        padding: 30px;
        background-color: #fff;
    }
</style>
