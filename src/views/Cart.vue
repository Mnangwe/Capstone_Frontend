<template>
  <Navbar/>
  <div class="container products" v-if="cart"  >
        <!-- <router-link class="card-wrapper" v-for="product of products" :to="{ name: 'Product', params: { id: product._id } }" :key="product._id"> -->
        <div class="row" v-if="cart">
          <div class="col-xs-12 col-sm-6 col-md-4 col-lg-3" v-for="cart in cart.products">
              <div class="card " style="width: 18rem;" >
              <!-- <img :src="product.image" class="card-img-top" alt="..."> -->
              <div class="card-body">
                <h3 class="card-title">{{item.name }} </h3>
                <!-- <p class="card-text">{{product.desc}}</p> -->
                <!-- <p class="card-price">R <span>{{product.price}}</span></p>
                <form class="card-quantity" @submit.prevent="addToCart(product._id)">
                  <input class="quantity" type="number" v-model="product.quantity" min="1">
                  <i class="fa fa-plus-square"></i>
                  <button type="submit" class="btn btn-primary" >Add to Cart</button>
                </form> -->
                </div>
              </div>
              </div>
          </div>
          
          
        <!-- </router-link> -->
      </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
export default {
  components: {
    Navbar
  },
  data() {
  return {
    user: JSON.parse(localStorage.getItem('user')),
    cart: null
  };
  },
  mounted() {
    if (localStorage.getItem("jwt")) {
      fetch(`https://capstone-estratweni.herokuapp.com/cart/${this.user._id}`, {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          console.log(json)
          this.cart = json.products
          console.log(this.cart)
        }).catch((err) => {
          alert("User not logged in");
        });
    }
    // } else {
    //   alert("User not logged in");
    //   this.$router.push({ name: "Home" });
    // }
  },

}
</script>

<style>

</style>