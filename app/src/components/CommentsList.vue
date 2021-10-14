<template>
    <div class="comments-list">
        <comments-card v-for="(comment, index) in commentsList" :key="comment.index" :index="index" :comment="comment" />
    </div>
</template>


<script>
import commentsListFile from '../data/comments.data.json'
import CommentsCard from './CommentsCard.vue'
export default {
    props: {
        index: Number,
    },
    components: {
        CommentsCard,
    },  
    data() {
        return {
            commentsList: commentsListFile
        }
    },
}
</script>
