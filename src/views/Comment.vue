<template>
    <div class="comment-view-wrapper">
        <div class="comment-view">
            <div class="content">
                <header>
                    <router-link :to="{ name: 'comments' }">
                        <img src="../assets/arrow-back.jpg" alt="">Back to comments
                    </router-link>
                    <DeleteBtn @click="deleteComment()"
                               title="Delete comment?"/>
                </header>
                <h1>{{ comment.title }}</h1>
                <p>{{ comment.body }}</p>
            </div>
            <hr>
            <h2>Lorem Ipsum is text of the typesetting industry</h2>
            <router-link :to="{ name: 'home' }">
                <ButtonBack title="Back to homepage"/>
            </router-link>
        </div>
    </div>
</template>

<script>
    import ButtonBack from "@/components/Button-back";
    import DeleteBtn from "@/components/Delete-btn";

    export default {
        name: "Comment",
        components: { DeleteBtn, ButtonBack },
        computed: {
            comment() {
                return this.$store.state.comment
            },
        },
        methods: {
            async deleteComment() {
                await this.$store.dispatch('deleteComment');
                this.$router.push({name: 'comments'});
            }
        },
        beforeRouteLeave(to, from, next) {
            if (to.name === 'comments') {
                this.$store.dispatch('getComments');
            }
            this.$store.commit('resetComment');
            next();
        },
        mounted() {
            return this.$store.dispatch('getComment', this.$route.params.id)
        }
    }
</script>

<style lang="scss" scoped>
    .comment-view-wrapper {
        flex-grow: 1;
        padding: 0 50px;

        .comment-view {
            text-align: left;
            max-width: 800px;
            margin: auto;

            .content {

                > header {
                    display: flex;
                    align-items: center;
                    justify-content: space-between;

                    > a {
                        color: black;
                        font-weight: 600;

                        img {
                            margin-right: 15px;
                        }
                    }
                }

                > h1 {
                    font-size: 3em;
                }

                > p {
                    font-weight: 500;
                }
            }

            > hr {
                border: 1px solid #4A4C5E;
                margin: 100px 0;
                opacity: .1;
            }

            > h2 {
                opacity: .5;
                margin: 0 0 40px 0;
                text-align: center;
            }

            > a {
                display: flex;
                margin-bottom: 100px;
                text-decoration: none;
                justify-content: center;
            }
        }
    }
</style>