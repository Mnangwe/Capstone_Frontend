<template>
  <Navbar/>
  <section class="store">
    <div class="container">
      <div class="row">
        <h2>This is Products</h2>
      </div>
      
      <div class="container" v-if="products"  v-for="product of products">
        <!-- <router-link class="card-wrapper" v-for="product of products" :to="{ name: 'Product', params: { id: product._id } }" :key="product._id"> -->
          <div class="card" style="width: 18rem;" >
            <img :src="product.image" class="card-img-top" alt="...">
            <div class="card-body">
              <h3 class="card-title">{{product.name}} </h3>
              <p class="card-text">{{product.desc}}</p>
              <p class="card-price">R <span>{{product.price}}</span></p>
              <form class="card-quantity" @submit.prevent="addToCart(product._id)">
                
                <input class="quantity" type="number" v-model="quantity" min="1">
                <i class="fa fa-plus-square"></i>
                <button type="submit" class="btn btn-primary" >Add to Cart</button>
              </form>
             
              
            </div>
          </div>
        <!-- </router-link> -->
      </div>

      <div class="row" v-else>
        Loading...
      </div>

    </div>
  </section>

</template>

<script>
import Navbar from "@/components/Navbar.vue"
export default {
  components: { Navbar },
  data() {
    return {
      user:JSON.parse(localStorage.getItem("user")),
      products: null,
      quantity: 1,
    };
  },
  methods: {
    addToCart(id){
      if (localStorage.getItem("jwt")) {
      console.log(this.user)
      const product = this.products.find(product => product._id === id)
      fetch(`https://capstone-estratweni.herokuapp.com/cart`, {
        method: "POST",
        body: JSON.stringify({
          userId: this.user._id,
          products: [
            {
              productId: product._id,
              quantity: this.quantity
            }
          ]
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          console.log(json);
          console.log(user)
          console.log("He is here")
        })
    }
  }
  },
  mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("https://capstone-estratweni.herokuapp.com/products", {
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
          
        //   fetch("http://localhost:3100/users/", {
        //   method: "GET",
        //   headers: {
        //     "Content-type": "application/json; charset=UTF-8",
        //     Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        //   },
        // }).then(res => res.json())
        // .then(data => {
        //     this.users = data
        //     console.log(data)
            
        //     })
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
.card {
  padding: 0;
}
.card-body {
  /* text-align: justify; */
}
.card img {
  width: 100%;
}
.card .card-title {
  font-weight: bold;
  color: #333;
}
.card-text {
  color: #999;
}
.card-price span {
  font-weight: bold;
  font-size: 25px;
}
.card-quantity {
  margin: 2px auto;
  display: flex;
  gap: 2px;
}
/* .card-quantity .iconify {
  height: 50px;
  width: 10px;
} */
.quantity {
  width: 25%;
  text-align: center;
}
</style>
