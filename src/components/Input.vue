<template>
  <input min="0" type="number" @input="changeAmount($event.target.value)" />
  <br />
  <button @click="convert()">Конвертировать</button>
</template>

<script>
export default {
  props: {
    changeAmount: {
      type: Function,
      required: true,
    },
    convert: {
      type: Function,
      required: true,
    },
  },
}
</script>

<style scoped>
input {
  width: 20rem;
  border: 0;
  border-radius: 3px;
  padding: 0.6rem 1rem;
  background-color: #fafafa;
  color: #333;
  outline: none;
}
button {
  padding: 0.5rem 1rem;
  background-color: rgba(80, 0, 136, 1);
  color: #fff;
  margin-top: 1rem;
  cursor: pointer;
}
</style>
