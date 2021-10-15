<template>
    <div class="comment-list">
        <transition name="fade">
        <div class="loading" v-show="loading">
            <div class="item item7">
                <div class="dot dot1"></div>
                <div class="dot dot2"></div>
                <div class="dot dot3"></div>
            </div>
        </div>
        </transition>
        <comment-card v-for="(comment, index) in commentItemsDisplayed" :key="comment.index" :index="index" :comment="comment" />
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
            loading: false,
            commentItemsDisplayed: [],
        }
    },
    mounted () {
        // Detect when scrolled to bottom.
        const listElm = document.querySelector('#infinite-list');
        listElm.addEventListener('scroll', () => {
          if(listElm.scrollTop + listElm.clientHeight >= listElm.scrollHeight) {
            this.loadMore();
          }
        })
          // Initially load some items.
        this.loadMore();
      },
      methods: {
        loadMore () {
          
          this.loading = true;
          setTimeout(() => {
            for (var i = 0; i < 20; i++) {
              this.commentItemsDisplayed.push(commentsListFile[i]);
            }
            this.loading = false;
          }, 1200);          
        }
      }
}
</script>

<style scoped>
    .comment-list{
        width: 100%;
        position: relative;
    }
    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s
    }
    .fade-enter, .fade-leave-to {
        opacity: 0
    }
    .loading{
        position: absolute;
        width: 50%;
        border-radius: 7px;
        background-color: rgba(65, 65, 65, 0.4);
        height: 15vh;
        left: 20%;
        bottom: 30vh;
    }
    .item {
        display: block;
        float: left;
        width: 80px;
        height: 80px;
        border-radius: 50%;
        background-color: white;
        box-sizing: border-box;
    }
    .item7 {
        z-index: 9;
        position: absolute;
        background: transparent;
        left: calc(50% - 45px);
        top: calc(50% - 35px);
    }
    .dot {
      width: 20px;
      height: 20px;
      display: block;
      position: absolute;
      top: 50%;
      border-radius: 50%;
      background-color: white;
      transform: translateY(-50%);
      animation: item7-dot 1.2s ease-in-out infinite;
    }
      .dot1 {
        left: 20%;
        transform: translateX(-50%);
      }
      .dot2 {
        left: 50%;
        transform: translateX(-50%);
        animation-delay: 0.2s;
      }
    .dot3 {
        transform: translateX(-50%);
        left: 80%;
        animation-delay: 0.4s;
    }
    @keyframes item7-dot {
        0% {
            opacity: 1;
            top: 50%;
        }
        50% {
            opacity: 0.3;
            top: 0;
        }
        100% {
            opacity: 1;
            top: 50%;
        }
    }
</style>