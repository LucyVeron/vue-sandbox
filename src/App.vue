<template>
  <h1>Store</h1>
  <div v-for="item in items" v-bind:key="item">
    <input v-model="item.stock">
    <span>{{item.name}}</span>
    <button v-on:click="add(item.name)">+</button>
    <button v-on:click="remove(item.name)">-</button>
  </div>
  <br>
  <span>Total inventory: {{ total }}</span>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      items: [
        {name: 'Compass', stock: 0},
        {name: 'Jacket', stock: 0},
        {name: 'Hiking Socks', stock: 0},
        {name: 'Suntan Lotion', stock: 0}
      ]
    }
  },
  computed() {
    return {
      total () {
        this.items.reduce((sum, product) => {
          return sum + product.stock
        })
      }
    }
  },
  methods: {
    add(name) {
      this.items.find((item) => item.name === name).stock++;
    },
    remove(name) {
      this.items.find((item) => item.name === name).stock--;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
