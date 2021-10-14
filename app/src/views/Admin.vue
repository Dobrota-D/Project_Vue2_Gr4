<template>
    <div class="admin">
        <h1> Admin page </h1>
        <crypto-list />
    </div>
</template>

<script>
    import CryptoList from '@/components/CryptoList.vue'
    
    export default {
        components: { CryptoList },
    }
</script>
