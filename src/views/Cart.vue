<template>
  <Navbar/>
  
</template>

<script>
import Navbar from '@/components/Navbar.vue'
export default {
  components: {
    Navbar
  },
  data() {
  return {
    products: null,
    user: JSON.parse(localStorage.getItem('user'))
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