<template>
  
  <div class="modal fade" id="editProfile" tabindex="-1" aria-labelledby="editProfileLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="editProfileLabel">Edit Product</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <form @submit.prevent="editProfile" class="modal-body">
        <input v-model="username" type="text" placeholder="username">
        <input v-model="email" type="text" Email...>
        <input v-model="profile" type="text" placeholder="profile picture">
        <input v-model="cover" type="text" placeholder="profile photo">
        <input v-model="password" type="text" placeholder="password">
        <button type="submit" class="btn btn-secondary" data-bs-dismiss="modal">Edit</button>
      </form>
      
    </div>
  </div>
</div>
</template>

<script>
export default {
  props:['user'],
  data(){
    return {
      username: this.user.username,
      email: this.user.email,
      profile: this.user.profile,
      cover: this.user.cover,
      password: null
    }
  },
  methods: {
      editProfile(){
      if (localStorage.getItem("jwt")){
              this.password = JSON.parse(localStorage.getItem("password"))
              fetch(`https://capstone-estratweni.herokuapp.com/users/${this.user._id}`, {
                  method: "PUT",
                  body: JSON.stringify({
                    username: this.username,
                    email: this.email,
                    profile: this.profile,
                    cover: this.cover,
                    password: this.password
                  }),
                  headers: {
                    "Content-type": "application/json; charset=UTF-8",
                    Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                  }
                }).then(res => res.json())
                  .then(data => {
                    console.log(data)
                    alert(data.msg)
                    localStorage.setItem("newUser", JSON.stringify(data.updateUser));
                    localStorage.removeItem('user');
                    location.reload()
                })

        }
      
      }
    }
}
</script>

<style>

</style>