<template>
    <div class="comment-card">
        <div class="title">{{title}}</div>
        <div class="description">{{description}}</div>
        <div class="content">{{content}}</div>
        <div class="author">{{author}}</div>
        <div class="date">{{date}}</div>
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
            this.date = this.getDate()
            this.content = this.comment.content
            
        },
        getDate(){
            const d = new Date(this.comment.date)
            const date = `${d.getDate()}/${d.getMonth()+1}/${d.getFullYear()} - ${d.getHours()}:${d.getMinutes()}` 
            return date
        }
    },

    mounted() {
      this.getCommentData()  
    },

}

</script>

<style scoped>
    .comment-card{
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.1);
        margin: 15px 0;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: white;
        border-radius: 7px;        
        
    }

    .title{
        font-weight: 800;
        font-size: 22px;
    }

    .date{

    }

    .description{

    }

    .author{

    }

    .content{

    }

</style>