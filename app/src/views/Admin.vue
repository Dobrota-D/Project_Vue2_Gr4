<template>
    <div class="admin">
        <div class="crypto-list-container">
            <crypto-list />
        </div>
        <div class="comments-list-container">
            <add-comment-form @newComment="addNewComment" />
            <comments-list />
        </div>
    </div>
</template>

<script>
import CryptoList from '@/components/CryptoList.vue'
import AddCommentForm from '../components/AddCommentForm.vue'
import CommentsList from '../components/CommentsList.vue'
import commentsListFile from '../data/comments.data.json'
    
    
    export default {
        components: { CryptoList, AddCommentForm, CommentsList },
        methods: {
            addNewComment(newComment) {
                // Add the new comment in the json file
                this.$set(commentsListFile, commentsListFile.length, newComment)
            }
        }
    }
</script>

<style scoped>
    body {
        display: flex;
        justify-content: center;
    }
    .crypto-list-container, .comments-list-container {
        display: inline-flex;
        flex-direction: column;
        width: 45%;
    }
    .crypto-list-container {
        margin-right: 3%;
    }
</style>
