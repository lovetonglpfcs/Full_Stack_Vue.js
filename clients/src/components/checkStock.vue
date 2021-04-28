<template>
  <div class="ctn">
      <div class="header">
        <div class="leftheader">
          <p class="blockheader">Check Stock</p>
        </div>
        <div class="rightheader">

          <router-link to="/"
            ><button
              class="blockheader"
            >
              Main Menu
            </button></router-link
          >
        </div>
      </div>
      <div class="Body">
        <div
          style="
            margin-top: 20px;
            margin-left: 45px;
            background-color: #9BC2EE;
            width: 95%;
            height: 900px;
          "
        >
      <table  border="1" >
        
        <Tbody>
          <tr >
            <td style="height:109px;width: 2000px;" v-for="(product) in products.slice(0,5)" :key="product._id">
              
                    <p style="font-weight:bold;margin: 0 0 0 0;">{{ product.name }}</p>
                    <p style="font-weight:bold;margin: 0 0 0 0;"  >Size : {{ product.size }}</p>
                    <p style="font-weight:bold;margin: 0 0 0 0;"  >Price : {{ product.price }}</p>

            </td>
            
          </tr>
        </Tbody>

        <thead>
          <tr>
            <td  style="height:270px;">
              <img src='../assets/img/makeorder/1.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/2.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/3.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/4.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/5.png' >
            </td>
            </tr>
            
        </thead>

      </table>

      <table  border="1" >
        
        <Tbody>
          <tr >
            <td style="height:109px;width: 2000px;" v-for="(product) in products.slice(5,10)" :key="product._id">
              
                    <p style="font-weight:bold;margin: 0 0 0 0;">{{ product.name }}</p>
                    <p style="font-weight:bold;margin: 0 0 0 0;"  >Size : {{ product.size }}</p>
                    <p style="font-weight:bold;margin: 0 0 0 0;"  >Price : {{ product.price }}</p>
                    
            </td>
            
          </tr>
        </Tbody>

        <thead>
          <tr>
            <td  style="height:270px;">
              <img src='../assets/img/makeorder/6.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/7.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/8.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/9.png' >
            </td>
            <td>
              <img src='../assets/img/makeorder/10.png' >
            </td>
            </tr>
            
        </thead>

      </table>
        
        </div>
      </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            products : [],
            insert: null,
            check: false,
            image : { img1: require('@/assets/img/makeorder/1.png') },
        }
    },
    methods: {
        handleClick(id){
            console.log(id);
        }
    },
    created(){
        let apiURL = 'http://localhost:4000/api';
        axios.get(apiURL).then(res => {
            this.products = res.data
            console.log(this.products)
        }).catch(error => {
            console.log(error)
        })
     },
     updated(){
       
       
    }
}
</script>

<style scoped>
button:hover {
  opacity: 0.5;
}
td{
  text-align: center;
}
.insert {
    background-color: #d6d831;
    border: 1px solid #111;
}
input {
    width: 50px;
    margin-right: 5px
}
p {
    font-weight:bold;
}
p:hover {
  cursor: default;
}
img {
    width: 250px;
}

.ctn {
  background-color: #002e69;
  width: 100%;
  height: 1100px;
  margin: 0;
  
}
.header {
  width: 100%;
  height: 150px;
  margin: 0;
}
.Body {
  width: 100%;
  height: 799px;
}
.leftheader {
  width: 50%;
  height: 100%;
  float: left;
}
.rightheader {
  width: 50%;
  height: 100%;
  float: left;
}

.blockheader {
  margin-left: 3%;
  margin-top: 0px;
  font-size: 40px;
  padding-top: 25px;
  text-align: center;
  border: 1px solid #111;
  width: 90%;
  height: 70%;
  color: rgb(255, 255, 255);
  background-color: #688CDE;;
}
.blockheader:hover {
  background-color: #688CDE;
}

.headerbutton {
  color: aliceblue;
  padding: 20px 30px;
  font-size: 25px;
  border-radius: 15px;
  border: 1px solid #000;
}

</style>