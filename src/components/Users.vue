<template>
  <section class="awesome-table">
        <table>
            <thead>
                <tr>
                    <th v-for="(obj, index) in configUser" :key="index">
                        {{ obj.title }}
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(row, index) in theData" :key="index">
                    <td v-for="(obj, ind) in configUser" :key="ind">
                        <span v-if="obj.type === 'text'">{{row[obj.key]}}</span>
                        <span v-if="obj.type === 'date'">{{new Date(row[obj.key]).toLocaleDateString()}} </span>
                        <figure v-if="obj.type === 'image'">
                            <img :src="row[obj.key]" height="60px">
                        </figure>
                        <div class="card-buttons">
                            <button v-if="obj.type === 'image'" type="submit" class="btn btn-primary">Edit Roles</button>
                            <button v-if="obj.type === 'image'" type="button" class="btn btn-primary" @click="deleteUser(row._id)">Delete</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </section>
</template>

<script>
export default {
    props: ['theData', 'configUser'],
    methods: {
        deleteUser(id){
          if(localStorage.getItem("jwt")){
            let confirmation = confirm(
            `Are you sure you want to remove this user from the list?`
            );

            if (confirmation) {
              fetch(`https://capstone-estratweni.herokuapp.com/${id}/user`, {
                method: "DELETE",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                }
            }).then(res => res.json())
              .then(async data => {
                await console.log(data)
                await console.log(data.msg)
                await location.reload()
              })
            }
              
          }
        },
        updateRole(id){
          if(localStorage.getItem("jwt")){
            const user = this.users.find(user => user._id === id)
            console.log(user)
            fetch(`https://capstone-estratweni.herokuapp.com/users/${id}/role`, {
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
    }
}
</script>

<style scoped>
    figure img {
        height: 60px;
        width: 60px;
        border: 1px solid #bbb;
        border-radius: 50%;
        overflow: hidden;
    }
    .awesome-table {
    border: 1px solid #999;
    border-radius: 4px;
    color: #333;
    overflow: auto;
    margin-top: 30px;
    }
    figure {
        margin-block-start: 0;
        margin-block-end: 0;
        margin-inline-start: 0;
        margin-inline-end: 0;
    }
    table {
        border-collapse: collapse;
        width: 100%;
    }
    table th {
        position: sticky;
        top: 0;
        background: #aaa;
        padding: 10px 5px;
        text-align: left;
        border-bottom: 1px solid #999;
    }
    table td {
        padding: 5px 5px;
        text-align: left;
    }
    table td:nth-child(4), table td:nth-child(2){
        font-weight: bold;
    }
    
</style>