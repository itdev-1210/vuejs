<template>
  <div class="container">
    <h3>Select Our Cool Beer!</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Name</th>
          <th scope="col">Image</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" v-bind:key="user.id">
          <th scope="row">{{user.id}}</th>
          <td>{{user.name}}</td>
          <td>
            <img v-bind:src="user.image_url" class="img-fluid" alt="Responsive image" />
          </td>
          <td>
            <router-link
              to="/detail"
              class="btn btn-primary detail"
              v-on:click.native="setDetail(user.id)"
            >Detail</router-link>
            <br />
            <button type="button" class="btn btn-warning add-cart" @click.prevent="addToCart">Add to cart</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",

  props: ["store"],

  data() {
    return {
      users: null,
      count: 0
    };
  },

  created: function() {
    axios
      .get("https://api.punkapi.com/v2/beers?page=1&per_page=10")
      .then(res => {
        this.users = res.data;
      });
  },

  methods: {
    addToCart: function() {
      this.store.addCount();
    },
    setDetail: function(num) {
      axios.get("https://api.punkapi.com/v2/beers/" + num).then(res => {
        this.store.setDetails(res.data);
      });
    }
  }
};
</script>

<style scoped>
.img-fluid {
  width: 80px;
  height: 300px;
}
.container h3 {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    color:rgb(19, 93, 230);
    text-align: center;
}
.table {
  text-align: center;
  vertical-align: middle;
}
.detail {
  margin-bottom: 10px;
  margin-top: 30px;
}
</style>