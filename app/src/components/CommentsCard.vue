<template>
    <div class="">
        
    </div>
</template>

<script>
import commentsListFile from '../data/comments.data.json'

export default {

    props: {
        comment: Object,
        index: Number
    },

    data() {
        return {
            commentsList : commentsListFile,
            author: '',
            title: '',
            description: '',
            content: '',
            date: '',
        }
    },

    methods: {
        getCommentData(){
            this.author = this.comment.author
            this.title = this.comment.title
            this.description = this.comment.description
            this.date = this.comment.date
            this.content = this.comment.content
        }
    },

    mounted() {
      this.getCommentData()  
    },

}

</script>