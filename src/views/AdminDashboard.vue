<template>
  <section class="admin-dashboard">

     <Navbar/>
    <div class="container admin">
      <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">
        <li class="nav-item" role="presentation">
          <button class="nav-link active" id="pills-home-tab" data-bs-toggle="pill" data-bs-target="#pills-home" type="button" role="tab" aria-controls="pills-home" aria-selected="true">Users</button>
        </li>
        <li class="nav-item" role="presentation">
          <button class="nav-link" id="pills-profile-tab" data-bs-toggle="pill" data-bs-target="#pills-profile" type="button" role="tab" aria-controls="pills-profile" aria-selected="false">Products</button>
        </li>
        <li class="nav-item" role="presentation">
          <button class="nav-link" id="pills-contact-tab" data-bs-toggle="pill" data-bs-target="#pills-contact" type="button" role="tab" aria-controls="pills-contact" aria-selected="false">Contact</button>
        </li>
      </ul>
      <!-- Users-tab -->
      <div class="tab-content" id="pills-tabContent">
        <div class="tab-pane fade show active" id="pills-home" role="tabpanel" aria-labelledby="pills-home-tab">
             <div class="users" v-if="users" >
              <div class="condainer" v-for="user of users">
                <div class="card" style="width: 18rem;" >
                  <img :src="user.profile" class="card-img-top" alt="...">
                  <div class="card-body">
                    <h3 class="card-title">{{user.username}} </h3>
                    <p class="card-text">{{user.email}}</p>
                    <div class="isAdmin">
                      <form @submit.prevent="updateRole(user._id)">
                        <div class="role-admin">
                          <input type="checkbox" name="" v-model="user.isAdmin">
                          <label v-if="user.isAdmin"> Admin</label>
                          <label v-else> Normal user</label>
                        </div>
                        <button type="submit" class="btn btn-primary">Edit Roles</button>
                      </form>
                    </div>
              <div class="card-quantity">
                {{user.isAdmin}}
              </div>
              <button type="button" class="btn btn-primary" @click="deleteUser(user._id)">Delete</button>
              
            </div>
          </div>
        </div>
        
    </div>
        </div>
        <!-- Products Tabs -->
        <div class="tab-pane fade" id="pills-profile" role="tabpanel" aria-labelledby="pills-profile-tab">
            <div class="products" v-if="products" >
              <div class="container" v-for="product of products">
                <div class="card" style="width: 18rem;" >
                <img :src="product.image" class="card-img-top" alt="...">
                <div class="card-body">
                  <h3 class="card-title">{{product.name}} </h3>
                  <p class="card-text">{{product.desc}}</p>
                  <p class="card-price">R <span>{{product.price}}</span></p>
                  <div class="card-quantity">
                    
                  
                </div>
                <button type="button" class="btn btn-primary" @click="deleteProduct(product._id)">Delete</button>
                <button type="button" class="btn btn-primary" @click="editProduct(product._id)">Edit</button>
              </div>
            </div>
          </div>
        
    </div>
        </div>
        <div class="tab-pane fade" id="pills-contact" role="tabpanel" aria-labelledby="pills-contact-tab">...</div>
      </div>
    </div>
    <!-- <div class="navigate">
        <button type="button" class="btn btn-primary" @click="findProducts">Products</button>
        <button type="button" class="btn btn-secondary" @click="findUsers">Users</button>
    </div> -->
  </section>
   
   

    
</template>

<script>
import Navbar from "@/components/Navbar"
export default {
    components: { Navbar },
    data() {
        return {
            users:null,
            products: null,
            income: null,
            admin:false
        }
    },
    methods: {
        deleteUser(id){
          if(localStorage.getItem("jwt")){
            let confirmation = confirm(
            `Are you sure you want to remove this user from the list?`
            );

            if (confirmation) {
              fetch(`http://localhost:3100/users/${id}/user`, {
                method: "DELETE",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                }
            }).then(res => res.json())
              .then(async data => {
                await console.log(data)
                await console.log(data.msg)
                location.reload()
              })
            }
              
          }
        },
        updateRole(id){
          if(localStorage.getItem("jwt")){
            const user = this.users.find(user => user._id === id)
            console.log(user)
            fetch(`http://localhost:3100/users/${id}/role`, {
              method: "PUT",
              body: JSON.stringify({
                isAdmin: user.isAdmin 
              }),
              headers: {
                "Content-type": "application/json; charset=UTF-8",
                Authorization: `Bearer ${localStorage.getItem("jwt")}`,
              }
            }).then(res => res.json())
              .then(data => console.log(data))
          }
        },
        deleteProduct(id){
          if(localStorage.getItem("jwt")){
            let confirmation = confirm(
            `Are you sure you want to remove this user from the list?`
            );

            if (confirmation) {
              fetch(`http://localhost:3100/products/${id}`, {
                method: "DELETE",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                }
            }).then(res => res.json())
              .then(async data => {
                await console.log(data)
                await console.log(data.msg)
                location.reload()
              })
            }
              
          }
        },
        editProduct(id){
          if(localStorage.getItem("jwt")){
            const product = this.products.find(user => user._id === id)
            console.log(user)
            fetch(`http://localhost:3100/users/${id}/role`, {
              method: "PUT",
              body: JSON.stringify({
                
              }),
              headers: {
                "Content-type": "application/json; charset=UTF-8",
                Authorization: `Bearer ${localStorage.getItem("jwt")}`,
              }
            }).then(res => res.json())
              .then(data => console.log(data))
          }
        }
    },
    mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("http://localhost:3100/users", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        }
      })
        .then((response) => response.json())
        .then((json) => {
          this.users = json;
          this.role = json.isAdmin
          console.log(json)
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
          console.log(this.products)
          console.log(json)
          fetch("http://localhost:3100/order/income", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.income = json;
          console.log(this.income)
        })
        
        })
        .catch((err) => {
          alert("User not logged in");
        });
        })
        }else {
      alert("User not logged in");
      this.$router.push({ name: "Home" });
    }
  }
}


</script>

<style>
.admin-dashboard {
  background: #eee;
  height: 100vh;
}
.navigate {
    position: relative;
    top: 0;
    left: 0;
    width: 100%;
    display: flex;
    flex-direction: row-reverse;
    padding-right: 20px;
    gap: 4px;
    margin: 5px;
}
.admin {
  padding-top: 10px;
  
}
.admin .nav {
  background: #aaa;
  border-radius: 5px;
}
.users {
    display: flex;
    gap: 4px;
    margin: 5px;
}
.products {
    display: flex;
    gap: 4px;
    margin: 5px;
}

</style>