<template>
  <section class="store">
    <div class="container">
      <div class="row">
        <h2>This is Products</h2>
      </div>
      
      <div class="row" v-if="products">
        <router-link class="card-wrapper" v-for="product of products" :to="{ name: 'Product', params: { id: product._id } }" :key="product._id">
          <div class="card" style="width: 18rem;">
            <img :src="product.image" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">{{product.name}} </h5>
              <p class="card-text">{{product.desc}}</p>
              <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </router-link>
      </div>

      <div class="row" v-else>
        Loading...
      </div>

    </div>
  </section>

</template>

<script>
export default {
  data() {
    return {
      products: null,
    };
  },
  mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("http://localhost:3100/products", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.products = json;
          console.log(json)
        }).catch((err) => {
          alert("User not logged in");
        });
    } else {
      alert("User not logged in");
      this.$router.push({ name: "Home" });
    }
  },

}
</script>

<style>
  

</style>
