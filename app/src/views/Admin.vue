<template>
    <div class="admin">
        <div class="crypto-list-container">
            <crypto-list />
        </div>
        <div class="comments-list-container">
        </div>
    </div>
</template>

<script>
import CryptoList from '@/components/CryptoList.vue'
    
    
    export default {
        components: { CryptoList },
    }
</script>

<style scoped>
    body {
        display: flex;
        justify-content: center;
    }
    .crypto-list-container, .comments-list-container {
        display: inline-flex;
        flex-direction: column;
        width: 45%;
    }
    .crypto-list-container {
        margin-right: 3%;
    }
</style>
