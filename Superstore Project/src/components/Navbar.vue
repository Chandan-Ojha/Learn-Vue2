<template>
  <!--Bootstrap Navbar-->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <!--<a class="navbar-brand" href="#">Super Store</a>-->
      <router-link class="navbar-brand" :to="{ path: '/'}">Super Store</router-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <!--Search-->
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <form @submit.prevent="search" class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="keyword">
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      keyword: ''
    }
  },
  methods: {
    search(){
      //this.$emit('search',this.keyword)
      var self = this;
      axios.get('http://localhost:3000/search/'+ this.keyword).then(response => {
        /*console.log(response.data)*/
        self.$store.commit('setInventory',response.data)
      })
    }
  }
}
</script>

<style>

</style>