<template>
    <header>
        <div class="logo">
            <router-link :to="{ name: 'home' }">
                <img src="../assets/logo.png" alt="">
            </router-link>
        </div>
        <nav>
            <router-link :to="{ name: 'home' }">ABOUT US</router-link>
            <router-link :to="{ name: 'write' }">WRITE COMMENT</router-link>
            <router-link :to="{ name: 'comments' }">COMMENTS</router-link>
        </nav>
    </header>
</template>

<script>
    export default {
        name: "Header",
        computed: {
            route() {
                return this.$route.name
            }
        }
    }
</script>

<style lang="scss" scoped>
    header {
        margin: 0 50px 50px;
        height: 66px;
        display: flex;
        justify-content: space-between;

        .logo {

        }

        nav {
            display: flex;
            align-items: center;

            a {
                color: black;
                font-weight: 500;
                margin-left: 30px;
                position: relative;
                text-decoration: none;
                text-transform: uppercase;

                &:before {
                    top: 0;
                    left: 0;
                    width: 0;
                    content: '';
                    height: 2px;
                    display: block;
                    transition: .3s;
                    margin-top: -20px;
                    position: absolute;
                    background-color: #F9D10D;
                }

                &.router-link-exact-active:before {
                    width: 100%;
                }
            }
        }
    }
</style>