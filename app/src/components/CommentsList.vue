<template>
    <div class="comment-list">
        <comment-card v-for="(comment, index) in commentsList" :key="comment.index" :index="index" :comment="comment" />
    </div>
</template>


<script>
import commentsListFile from '../data/comments.data.json'
import CommentCard from './CommentsCard.vue'
export default {
    props: {
        index: Number,
    },
    components: {
        CommentCard,
    },  
    data() {
        return {
            commentsList: commentsListFile
        }
    },
}
</script>

<style scoped>
    .comment-list{
        width: 40%;
    }
</style>