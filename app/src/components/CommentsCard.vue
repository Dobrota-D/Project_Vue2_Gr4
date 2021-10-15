<template>
    <div class="comment-card" @newContent="setNewContent">
        <div class="comment-data">
            <a :href="comment.url" target="_blank"><img :src="comment.urlToImage" v-if="this.$route.path === '/'" alt="comment-img"></a>
            <div class="comment-info">
                <div class="title">{{comment.title}}</div>
                <div class="description">{{comment.description}}</div>
                <div class="content">{{content}}</div>
                <div class="comment-data-and-author">
                    <div class="author">{{comment.author}}</div>
                    <div class="date">{{date}}</div>
                </div>
            </div>
        </div>
        <div class="comment-admin-view" v-if="this.$route.path === '/admin'">
            <div class="delete-comment" @click="deleteComment">
                <svg width="24" height="24" fill="none" viewBox="0 0 24 24"><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6.75 7.75L7.59115 17.4233C7.68102 18.4568 8.54622 19.25 9.58363 19.25H14.4164C15.4538 19.25 16.319 18.4568 16.4088 17.4233L17.25 7.75"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9.75 7.5V6.75C9.75 5.64543 10.6454 4.75 11.75 4.75H12.25C13.3546 4.75 14.25 5.64543 14.25 6.75V7.5"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 7.75H19"></path></svg>
            </div>
            <div class="modify-comment"  @click="showModifyCommentTextarea = true">
                <svg width="24" height="24" fill="none" viewBox="0 0 24 24"><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.75 19.25L9 18.25L18.2929 8.95711C18.6834 8.56658 18.6834 7.93342 18.2929 7.54289L16.4571 5.70711C16.0666 5.31658 15.4334 5.31658 15.0429 5.70711L5.75 15L4.75 19.25Z"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19.25 19.25H13.75"></path></svg>
            </div>
        </div>
        <div class="modify-comment-textarea" v-if="showModifyCommentTextarea">
            <textarea cols="30" rows="10" v-model="content"></textarea>
            <button @click="modifyContent">Enregistrer</button>
        </div>
    </div>
</template>

<script>
import commentsListFile from '../data/comments.data.json'

export default {
    props: {
        comment: Object,
        index: Number,
    },
    data() {
        return {
            commentsList : commentsListFile,
            date: '',
            content: '',
            showModifyCommentTextarea: false
        }
    },

    methods: {
        getCommentData(){
            this.date = this.getDate()
            this.content = this.comment.content
        },
        getDate(){
            const d = new Date(this.comment.date)
            const months = ["janvier","février","mars","avril","mai","juin","juillet","août","septembre","octobre","novenbre","Décembre"]

            const day = d.getDate() < 10 ? '0' + d.getDate() : d.getDate()
            const month = months[d.getMonth()]
            const hours = d.getHours() < 10 ? '0' + d.getHours() : d.getHours()
            const minutes = d.getMinutes() < 10 ? '0' + d.getMinutes() : d.getMinutes()

            const date = `${day} ${month} ${d.getFullYear()} - ${hours}h${minutes}`
            return date
        },
        deleteComment() {
            this.$delete(this.commentsList, this.index)
        },
        setNewContent(newContent) {
            this.content = newContent
        },
        modifyContent() {
            this.showModifyCommentTextarea = false
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
    .comment-info {
        padding: 10px 20px;  
    }
    .comment-admin-view {
        width: 10%;
    }
    img {
        width: 111%;
        border-radius: 7px 7px 0 0;
    }
    .title{
        font-weight: 900;
        font-size: 22px;
    }
    .description {
        color: grey;
        font-size: 13px;
        text-align: left;
        margin: 10px 0;
    }
    .content {
        text-align: justify;
    }
    .comment-data-and-author {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        color: grey;
        font-size: 13px;
        margin: 15px 0;
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
    .modify-comment-textarea {
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        background-color: rgba(0, 0, 0, .8);
        width: 100%;
        height: 100vh;
    }
    textarea {
        border-radius: 7px;
        outline: none;
        border: none;
        width: 50%;
        height: 50vh;
        padding: 10px;
    }
    button {
        margin: 10px 0;
        background-color: #0d6efd;
        border: none;
        border-radius: 7px;
        cursor: pointer;
        padding: 10px 15px;
        font-weight: 600;
        color: white;
        width: fit-content;
        position: relative;
        left: 22%;
    }
</style>