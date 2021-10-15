<template>
    <div class="comment-list">
        <comment-card v-for="(comment, index) in commentsList" :key="comment.index" :index="index" :comment="comment" />
    </div>
</template>

<script>
import commentsListFile from '../data/comments.data.json'
import CommentCard from './CommentsCard.vue'

export default {
    components: {
        CommentCard,
    },
    data() {
        return {
            commentsList: commentsListFile,
        }
    },
}
</script>

<style scoped>
    .comment-list{
        width: 100%;
    }
</style>