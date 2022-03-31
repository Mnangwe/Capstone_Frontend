<template>
  <Navbar/>
  <div class="container-fluid products" v-if="cart"  >
        <!-- <router-link class="card-wrapper" v-for="product of products" :to="{ name: 'Product', params: { id: product._id } }" :key="product._id"> -->
        <div class="container" v-if="cart">
          <div class="card-wrapper" >
              <div class="card row" v-for="product in cart.products">
                <div class="image col-md-2">
                  <img :src="product.image" class="card-img-top" alt="...">
                </div>
                <div class="col-md-10">
                  <div class="row">
                    <div class="card-body col-md-8">
                      <div class="naming">
                        <h3 class="card-title">{{product.name}}</h3>
                      </div>

                      <div class="cart-price">
                        <p class="card-price">R <span>{{product.price}}</span></p>
                        <form class="card-quantity" @submit.prevent="addToCart(product._id)">
                          <input class="quantity" type="number" v-model="product.quantity" min="1">
                          <i class="fa fa-plus-square"></i>
                          <button type="submit" class="btn btn-primary" ><span class="iconify" data-icon="ant-design:plus-square-filled"></span></button>
                        </form> 
                      </div>

                      

                    </div>
                    <div class="row">
                      <div class="col-md-10 description">
                        <p class="card-text">{{product.desc}}</p>
                      </div>
                    </div>
                  </div>
                </div>
                
                
              </div>
          </div>
        </div>
          
          
        <!-- </router-link>  -->
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
  methods: {
    updateQuantity(id){
      
    }
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
          this.cart = json
          console.log(this.cart)
        }).catch((err) => {
          alert("User not logged in");
        });
    }
     else {
      alert("User not logged in");
      this.$router.push({ name: "Home" });
    }
  },

}
</script>

<style scoped>
  /* .card-wrapper {
    display: flex;
    flex-direction: column;
    margin-bottom: 5px;
    
  } */
  .card {
    width: 100%;
    display: flex;
    flex-direction: row;
    margin-bottom: 10px;
    margin-top: 10px;
    border-radius: 10px;
    box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px, rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px, rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
  }
  .image img {
    height: 100%;
    width: 100%;
    border-radius: 10px 0 0 10px;
  }
  .image {
    padding-left: 0;
  }
  .card-body {
    display: flex;
    justify-content: space-between;
  }
  .cart-price {
    display: flex;
  }
  .description {
    text-align: left;
    color: #888;
  }
</style>