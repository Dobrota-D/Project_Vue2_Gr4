<template>
  <div class="home">
    <crypto-list />
    <comments-list/>
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
