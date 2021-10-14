<template>
  <div class="home">

    <crypto-list />
  </div>
</template>

<script>
// @ is an alias to /src
    import CryptoList from '@/components/CryptoList.vue'
    
    export default {
        components: { CryptoList },
    }
</script>
