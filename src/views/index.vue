<template>
  <div>
    <div id="nav">
      <img src="../assets/logo.png" alt="Logo YTS">
      <div class="button">Jadwal Siaran</div>
    </div>

    <div id="content">
      <div class="header">
        <h2>Jadwal Siaran</h2>
        <div class="account button">
          <i class="fa fa-user-circle"></i>
          {{ account }}

          <div class="logout button">
            <i class="fa fa-power-off"></i>
            Logout
          </div>
        </div>
      </div>

      <div class="list">
        <table border="1">
          <tr>
            <td>No</td>
            <td>Tanggal</td>
            <td>Mulai</td>
            <td>Selesai</td>
            <td>Judul</td>
            <td>Nama Ustadz</td>
            <td>Jenis</td>
            <td>Aksi</td>
          </tr>
          <tr v-for="(item, id) in items" :key="id">
            <td>{{ item.id }}</td>
            <td>{{ item.name}}</td>
            <td>{{ item.address.street }}</td>
            <td>{{ item.address.suite }}</td>
            <td>{{ item.phone }}</td>
            <td>{{ item.website }}</td>
            <td>{{ item.email }}</td>
            <td></td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data(){
    return{
      account: "Admin",
      items: null
    }
  },
  mounted(){
    axios
    .get('https://jsonplaceholder.typicode.com/users')
    .then(response => (
      this.items = response,
      console.log(response)
      ))
    .catch(error => console.log(error));
  }
}
</script>
<style scoped>
  *{
    margin: 0;
  }
  table{
    border-collapse: collapse;
  }
  td{
    padding: 10px 20px;
  }
  #nav{
    float: left;;
    width: 20%;
    min-height: 657px;
    box-shadow: 4px -4px 8px 0 #00000028;
    /* padding: 20px; */
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  #content{
    float: left;
    width: 80%;
  }
  .header{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 50px;
  }
  .button{
    width:fit-content;
    background-color: #44693D;
    color:white;
    padding: 8px 35px;
    border-radius: 15px;
    font-size: 20px;
  }
  .account{
    position: relative;
  }
  .account:hover{
    box-shadow: 0 0 8px 5px #00000028;
    border-radius: 20px 20px 0 0;
  }
  .account:hover .logout{
    display: block;
    
  }
  .logout{
    /* display: none; */
    position: absolute;
    display: none;
    left: 0;
    top: 40px;
    width: inherit;
    padding-right: 32px;
    padding-left: 32px;
    background-color: rgb(251, 0, 0);
    border-radius: 0 0 20px 20px;
  }
  .list{
    width: fit-content;
    margin: auto;
  }
</style>