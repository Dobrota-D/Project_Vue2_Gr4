<template>
  <div class="home">
    <crypto-list />
  </div>
</template>

<script>
    import CryptoList from '@/components/CryptoList.vue'
    
    export default {
        components: { CryptoList },
    }
</script>
