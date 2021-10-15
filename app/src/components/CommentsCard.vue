<template>
    <div class="comment-card">
        <div class="comment-data">
            <div class="title">{{title}}</div>
            <div class="description">{{description}}</div>
            <div class="content">{{content}}</div>
            <div class="author">{{author}}</div>
            <div class="date">{{date}}</div>
        </div>
        <div class="comment-admin-view" v-if="this.$route.path === '/admin'">
            <div class="delete-comment" @click="deleteComment">
                <svg width="24" height="24" fill="none" viewBox="0 0 24 24"><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6.75 7.75L7.59115 17.4233C7.68102 18.4568 8.54622 19.25 9.58363 19.25H14.4164C15.4538 19.25 16.319 18.4568 16.4088 17.4233L17.25 7.75"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9.75 7.5V6.75C9.75 5.64543 10.6454 4.75 11.75 4.75H12.25C13.3546 4.75 14.25 5.64543 14.25 6.75V7.5"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 7.75H19"></path></svg>
            </div>
            <div class="modify-comment"  @click="modifyComment">
                <svg width="24" height="24" fill="none" viewBox="0 0 24 24"><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.75 19.25L9 18.25L18.2929 8.95711C18.6834 8.56658 18.6834 7.93342 18.2929 7.54289L16.4571 5.70711C16.0666 5.31658 15.4334 5.31658 15.0429 5.70711L5.75 15L4.75 19.25Z"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19.25 19.25H13.75"></path></svg>
            </div>
        </div>
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
        },
        deleteComment() {
            console.log('delete comment');
        },
        modifyComment() {
            console.log('Modify comment');
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
        background-color: white;
        border-radius: 7px;        
    }
    .comment-data {
        width: 90%;
    }
    .comment-admin-view {
        width: 10%;
    }
    .title{
        font-weight: 800;
        font-size: 22px;
    }
    .delete-comment, .modify-comment {
        width: 100%;
        height: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
    }
    .delete-comment {
        background-color: #ff3535;
        border-top-right-radius: 7px;
    }
    .modify-comment {
        background-color: #0d6efd;
        border-bottom-right-radius: 7px;
    }
</style>