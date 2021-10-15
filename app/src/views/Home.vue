<template>
  <div class="home">
    <div class="crypto-list-container">
      <crypto-list />
    </div>
    <div class="comment-list-container">
      <comments-list />
    </div>
  </div>
</template>

<script>
    import CryptoList from '@/components/CryptoList.vue'
    import CommentsList from '../components/CommentsList.vue'
    //import CommentsList from '@/components/CommentList.vue'

    export default {
        components: { CryptoList, CommentsList },

    }
</script>

<style>
  .home{
    display: flex;
    justify-content: space-around;
  }
  .crypto-list-container, .comment-list-container {
    width: 40%;
  }
</style>