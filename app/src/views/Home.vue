<template>
  <div class="home">
    <div class="crypto-list-container">
      <crypto-list />
    </div>
    <div class="comment-list-container" id="infinite-list">
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
    height: 75vh;
    overflow-y: scroll;
    padding-inline: 20px;
    box-shadow: 0 0 20px 0 rgba(0, 0, 0, .1);
    background-color: rgba(214, 219, 222, 0.5);
    border-radius: 7px;
  }
</style>