<template>
  <div class="container">
    <h3>Welcome to detail page!</h3>
    <div class="detail">
      <div class="description">
        <ul v-for="detail in store.details" v-bind:key="detail.id">
          <li>Name: {{detail.name}}</li>
          <li>First Brewed: {{detail.first_brewed}}</li>
          <li>Description: {{detail.description}}</li>
          <li>Yeast: {{detail.ingredients.yeast}}</li>
          <li>Brewer Tips: {{detail.brewers_tips}}</li>
          <li>Contributed By: {{detail.contributed_by}}</li>
        </ul>
      </div>
      <div class="image">
        <ul v-for="detail in store.details" v-bind:key="detail.id">
          <li>
            <img v-bind:src="detail.image_url" class="img-fluid" alt="Responsive image" />
          </li>
        </ul>
      </div>
    </div>
    <div class="clearbox"></div>
    <button type="button" class="btn btn-warning add-cart" @click.prevent="addToCart">Add to cart</button>
  </div>
</template>

<script>
export default {
  name: "Detail",
  data() {
    return {
      details: null
    };
  },
  props: ["store"],
  created: function() {},
  methods: {
    addToCart: function() {
      this.store.addCount();
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
  color: rgb(19, 93, 230);
  text-align: center;
  margin-bottom: 50px;
}
.add-cart {
  margin: 50px;
  margin-left:60%;
}
ul {
  list-style-type: none;
  padding: 0;
}
.description {
  width: 55%;
  float: right;
  text-align: left;
  padding: 20px;
}
.image {
  width: 35%;
  float: left;
  text-align: center;
  background-color: aqua;
  border-radius: 50%;
  padding: 30px;

  margin-left: 70px;
}
.clearbox {
  clear: both;
}
</style>