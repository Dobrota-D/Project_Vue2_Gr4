<template>
    <div class="crypto-card">
        <div class="crypto-card-left" @click="goToCrypto(crypto.abbreviation)">
            <div class="crypto-data">
                <img :src="crypto.icon" :alt="crypto.abbreviation + '-icon'">
                <div class="crypto-name">
                    <p>{{ crypto.name }}</p>
                    <p>{{ crypto.abbreviation }}</p>
                </div>
            </div>
            <div class="crypto-price">
                <p>{{ cryptoPrice }}€</p>
            </div>
        </div>
        <div class="delete-crypto" @click="deleteCrypto" v-if="this.$route.path === '/admin'">
            <svg width="24" height="24" fill="none" viewBox="0 0 24 24"><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6.75 7.75L7.59115 17.4233C7.68102 18.4568 8.54622 19.25 9.58363 19.25H14.4164C15.4538 19.25 16.319 18.4568 16.4088 17.4233L17.25 7.75"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9.75 7.5V6.75C9.75 5.64543 10.6454 4.75 11.75 4.75H12.25C13.3546 4.75 14.25 5.64543 14.25 6.75V7.5"></path><path stroke="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 7.75H19"></path></svg>
        </div>
    </div>
</template>


<script>
import cryptoListFile from '../data/crypto.data.json'
import router from '../router/index.js'

export default {
    props: {
        crypto: Object,
        index: Number
    },
    methods: {
        getCryptoData(cryptoAbb) {
            fetch(`https://api.coinbase.com/v2/prices/${cryptoAbb}-EUR/spot`)
            .then(res => res.json())
            .then(result => this.cryptoPrice = result.data.amount )
        },
        deleteCrypto() {
            this.$delete(this.cryptoList, this.index)
        },
        goToCrypto(cryptoAbb){
            router.push({ name: 'crypto', params:{ cryptoAbb : cryptoAbb}})
        }
    },
    mounted() {
        this.getCryptoData(this.crypto.abbreviation)
    },
    data() {
        return {
            cryptoPrice: 0,
            cryptoList: cryptoListFile
        }
    }
}
</script>

<style scoped>
    p {
        margin: 0;
    }
    .crypto-card {
        display: flex;
        justify-content: space-between;
        background-color: white;
        border-radius: 7px;
        margin: 15px 0;
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, .1);
        cursor: pointer;
    }
    .crypto-card-left {
        padding: 20px;
        width: calc(90% - 40px);
        display: flex;
        justify-content: space-between;
    }
    .crypto-data {
        display: flex;
        align-items: center;
    }
    .crypto-data img {
        width: 40px;
        height: 40px;
        margin-right: 10px;
    }
    .crypto-name {
        display: flex;
        flex-direction: column;
    }
    .crypto-name p {
        display: flex;
    }
    .crypto-price {
        display: flex;
        align-items: center;
    }
    .delete-crypto {
        background-color: #ff3535;
        width: 10%;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 0 7px 7px 0;
        cursor: pointer;
    }
</style>