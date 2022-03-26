<template>
  <div class="modal fade" id="editProfile" tabindex="-1" aria-labelledby="editProfileLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="editProfileLabel">Edit Product</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <form @submit.prevent="editProfile()" class="modal-body">
        <input v-model="username" type="text" placeholder="username">
        <input v-model="email" type="text" Email...>
        <input v-model="profile" type="text" placeholder="profile picture">
        <input v-model="cover" type="text" placeholder="profile photo">
        <input v-model="password" type="text" password>
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Edit</button>
      </form>
      
    </div>
  </div>
</div>
</template>

<script>
export default {
    methods: {
        editProfile(){
        if (localStorage.getItem("jwt")){
            
            
            }
        }
        
    }
}
</script>

<style>

</style>