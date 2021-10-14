<template>
    <div class="crypto-card">
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
</template>


<script>
export default {
    props: {
        crypto: Object
    },
    methods: {
        getCryptoData(cryptoAbb) {
            fetch(`https://api.coinbase.com/v2/prices/${cryptoAbb}-EUR/spot`)
            .then(res => res.json())
            .then(result => this.cryptoPrice = result.data.amount )
        }
    },
    mounted() {
        this.getCryptoData(this.crypto.abbreviation)
    },
    data() {
        return {
            cryptoPrice: 0
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
        padding: 20px;
        margin: 15px 0;
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, .1);
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
</style>