<template>
  <div class="container">
    <h2>Welcome to Our Market!</h2>
    <span> Cart </span>
    <button type="button" class="btn btn-info">{{store.count}}</button>
  </div>
</template>

<script>

export default {
  props: ["store"],
  name: "Header"
};
</script>

<style scoped>
.container {
    background-color: burlywood;
    padding: 20px;
    margin-bottom: 40px;
    
}
.container h2 {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    color:indigo;
    display: inline-block;
}
.container span {
    margin-left: 50%;
    margin-right: 10px;
    font-size: 20px;
    font-weight: 700;
}
.container button {
    font-size: 18px;
    border-radius: 50%;
    width: 40px;
    text-align: center;
    padding: 5px;
}


</style>