<template>
    <div class="container">
        <img :src="infoCrypto.icon" alt="IconCrypto">
        <h1> {{ infoCrypto.name }}  {{ infoCrypto.abbreviation }} </h1>
        <h3> {{ infoCrypto.price }} € </h3>
    </div>
</template>

<script>
import cryptoList from '../data/crypto.data.json'
import router from '../router/index.js'

export default {
    methods: {
        checkCryptoExist() {
        let foundedCrypto = false;
        cryptoList.forEach(crypto => {
            if (crypto.abbreviation === this.actualCrypto) {
                this.infoCrypto.name = crypto.name
                this.infoCrypto.abbreviation = crypto.abbreviation
                this.infoCrypto.icon = crypto.icon
                this.getInfoCrypto(this.actualCrypto)
                foundedCrypto = true
            }
        });
        return foundedCrypto
        },
        getInfoCrypto(cryptoName){
            fetch(`https://api.coinbase.com/v2/prices/${cryptoName}-EUR/spot`).catch(() => console.log(cryptoName))
            .then(res => res.json())
            .then(res => this.infoCrypto.price = res.data.amount)
        }
    },
  mounted(){
    let currentUrl = window.location.pathname
    this.actualCrypto = currentUrl.substring(8).toUpperCase()
    if (!this.checkCryptoExist()) {
        router.push({ name: 'NotFound', params:{ 0 : "NotFound"}})
    }
  },
  data(){
    return {
      actualCrypto: '',
      infoCrypto: {
          name: '',
          abbreviation: '',
          icon: '',
          price: 0,
      }
    }
  },
}
</script>