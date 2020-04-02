<template>
  <div id="app" class="container">
    <Header v-bind:store="store"/>
    <router-view v-bind:store="store"/>
  </div>
</template>

<script>
import Header from "./components/Header";

export default {
  name: "app",
  data() {
    return {
      store: {
        count:0,
        details:null,
        addCount(){
          this.count=this.count+1
        },
        setDetails(des){
          this.details=des
        }
      }
    };
  },
  components: {
    Header
  }
};
</script>

<style>
 #app {
  background-color: blanchedalmond;
  padding: 0;
} 
</style>
