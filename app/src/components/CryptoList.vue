<template>
    <div class="crypto-list">
        <crypto-card v-for="(crypto, index) in cryptoList" :key="crypto.name" :crypto="crypto" :index="index" />
    </div>
</template>

<script>
    import cryptoListFile from '../data/crypto.data.json'
    import CryptoCard from './CryptoCard.vue';

export default {
    components: { CryptoCard },
    data() {
        return {
            cryptoList: cryptoListFile,
        }
    },
}
</script>

<style scoped>
    .crypto-list{
        width: 100%;
    }
</style>