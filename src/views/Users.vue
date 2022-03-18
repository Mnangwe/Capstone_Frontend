<template>
  <div >
    <div class="row">Users Page</div>
    <TableUsers v-if="tableData" :theData="tableData" :config="config" :style="{height: '600px'}"/>
  </div>
</template>

<script>
import TableUsers from '../components/TableUsers.vue'
import axios from 'axios'
export default {
  components: {
    TableUsers
  },
  data: () => ({
    tableData: undefined,
    config: [
      {
        key: 'avatar',
        title: 'Avatar',
        type: 'image'
      },
      {
        key: 'name',
        title: 'Name',
        type: 'text'
      },
      {
        key: 'city',
        title: 'City',
        type: 'text'
      },
      {
        key: 'companyName',
        title: 'Company',
        type: 'text'
      },
      {
        key: 'createdAt',
        title: 'Signup Date',
        type: 'date'
      }
    ]
  }),
  mounted () {
     fetch("http://localhost:3100/users", {
          method: "GET",
          headers: {
            "Content-type": "application/json; charset=UTF-8",
            // Authorization: `Bearer ${localStorage.getItem("jwt")}`,
          },
        })
          .then((response) => response.json())
          .then((json) => {
            this.tableData = json;
            console.log(this.tableData)
          })
  }
}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
  font-weight: 400;
}
</style>
