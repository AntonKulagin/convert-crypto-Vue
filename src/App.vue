<template>
  <h1>CRYPTO</h1>

  <Input :changeAmount="changeAmount" :convert="convert" />
  <p v-if="error !== ''" className="error">{{ error }}</p>
  <p v-if="result !== 0" className="result">
    From {{ cryptoFirst }} to {{ cryptoSecond }}: <span>{{ result }}</span>
  </p>
  <div className="selectors">
    <Selector :setCrypto="setCryptoFirst" />
    <Selector :setCrypto="setCryptoSecond" />
  </div>
</template>

<script>
import Input from './components/Input.vue'
import Selector from './components/Selector.vue'
import CryptoConvert from 'crypto-convert'

const convert = new CryptoConvert()

export default {
  components: { Input, Selector },
  data() {
    return {
      amount: 0,
      cryptoFirst: '',
      cryptoSecond: '',
      error: '',
      result: 0,
    }
  },
  methods: {
    changeAmount(val) {
      this.amount = val
    },
    setCryptoFirst(val) {
      this.result = 0
      this.cryptoFirst = val
    },
    setCryptoSecond(val) {
      this.result = 0
      this.cryptoSecond = val
    },
    async convert() {
      if (this.amount <= 0) {
        this.error = 'Введите число больше 0'
        return
      } else if (this.cryptoFirst === '' || this.cryptoSecond === '') {
        this.error = 'Выберете валюту'
        return
      } else if (this.cryptoFirst === this.cryptoSecond) {
        this.error = 'Выберете другую валюту'
        return
      }
      this.error = ''

      await convert.ready()
      this.result = convert[this.cryptoFirst][this.cryptoSecond](this.amount)
    },
  },
}
</script>

<style scoped>
.selectors {
  display: flex;
  justify-content: space-between;
  gap: 0.5rem;
  width: 25rem;
  margin: 0 auto;
}
.error {
  color: red;
}
span {
  font-family: Nabla, sans-serif;
  font-size: 2rem;
}
</style>
