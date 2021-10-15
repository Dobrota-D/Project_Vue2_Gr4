<template>
    <div class="admin">
        <div class="crypto-list-container">
            <crypto-list />
        </div>
        <div class="comments-list-container">
            <add-comment-form />
            <comments-list />
        </div>
    </div>
</template>

<script>
import CryptoList from '@/components/CryptoList.vue'
import AddCommentForm from '../components/AddCommentForm.vue'
import CommentsList from '../components/CommentsList.vue'
    
    
    export default {
        components: { CryptoList, AddCommentForm, CommentsList },
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
