<template>
  <ul>
    <li @click="setItem('BTC')" :className="current === 'BTC' ? 'active' : ''">
      Bitcoin
    </li>
    <li @click="setItem('ETH')" :className="current === 'ETH' ? 'active' : ''">
      ETH
    </li>
    <li
      @click="setItem('USDT')"
      :className="current === 'USDT' ? 'active' : ''"
    >
      USDT
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    setCrypto: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      current: '',
    }
  },

  methods: {
    setItem(val) {
      this.setCrypto(val)
      this.current = val
    },
  },
}
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  background-color: #222;
  width: 10rem;
}
li {
  line-height: 2rem;
  padding: 0.5rem;
}
li:hover,
li:active,
li.active {
  background-color: #333;
  cursor: pointer;
}
</style>
