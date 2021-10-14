<template>
    <div class="crypto-list">
        <crypto-card v-for="crypto in cryptoList" :key="crypto.name" :crypto="crypto" />
    </div>
</template>

<script>
    import cryptoListFile from '../data/crypto.data.json'
    import CryptoCard from './CryptoCard.vue';

export default {
    props: {
        nom: String,
        x: Array
    },
    components: { CryptoCard },
    data() {
        return {
            cryptoList: cryptoListFile,
        }
    },
}
</script>

<style scoped>
    .crypto-list {
        width: 45%;
    }
</style>
