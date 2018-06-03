<template>
  <div id="app">
    <div v-if="lists.length>0">
        <table>
          <thead>
            <tr>
              <th></th>
              <th>Product Name</th>
              <th>Price</th>
              <th>Quantity</th>
              <th>Action</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in lists">
              <td>{{index+1}}</td>
              <td>{{item.name}}</td>
              <td>{{item.price}}</td>
              <td>
                <button 
                  @click="handleReduce(index)"
                  :disabled="item.count ==1">-</button>
                  {{item.count}}
                <button @click="handleAdd(index)">+</button>
              </td>
              <td>
                <button @click="handleRemove(index)">Remove</button>
              </td>
            </tr>
          </tbody>
        </table>
        <div>Total price : {{totalPrice}}</div>
    </div>
    <div v-else>Shopping cart is empty!</div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      lists: [
        { id: 1, name: "iPhone 6", price: 6288, count: 2 },
        { id: 2, name: "iPad Prd", price: 7288, count: 1 },
        { id: 3, name: "MacBook Pro", price: 15288, count: 1 }
      ]
    };
  },
  computed: {
    totalPrice: function() {
      const sum = (acc, cur) => cur.price * cur.count + acc;
      return this.lists.reduce(sum, 0);
    }
  },
  methods: {
    handleReduce: function(index) {
      this.lists[index].count--;
    },
    handleAdd: function(index) {
      this.lists[index].count++;
    },
    handleRemove: function(index) {
      this.lists.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
