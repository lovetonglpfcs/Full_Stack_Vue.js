<template>
  <div class="ctn">
    <div class="header">
      <div class="leftheader">
        <p class="blockheader">History Sale</p>
      </div>
      <div class="rightheader">
        <router-link to="/"
          ><button
            class="blockheader"
            style="background-color: #909CA6;"
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
          background-color: #D5E7F5;
          width: 95%;
          height: 95%;
        "
      >
        <pre></pre>
        <table align="center" style="background: white; margin-top: 10px">
          <tr style="font-weight: bold; font-size: 18px">
            <td style="width: 100px">รายการที่</td>
            <td style="width: 300px">ชื่อ</td>
            <td style="width: 400px">รายกายที่ซื้อ</td>
            <td style="width: 100px">Size</td>
            <td style="width: 100px">จำนวนตัว</td>
            <td style="width: 125px">ราคา</td>
            <td style="width: 250px">วันที่</td>
            <td
              style="width: 100px;"
            ></td>
          </tr>

          <tr
            v-for="(history, i) in histories"
            :key="history._id"
            style="font-size: 17px"
          >
            <td>{{ i + 1 }}</td>
            <td>{{ history.customer }}</td>
            <td style="text-align: left;">{{ history.name }}</td>
            <td>{{ history.size }}</td>
            <td>{{ history.numberofunit }}</td>
            <td>{{ history.price }}</td>
            <td>
              {{ history.date.slice(0, 10) }}
            </td>
            <td><div class="delete" @click="handleDelete(history._id)" style="">Delete</div></td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      histories: [],
      
    };
  },
  methods: {
    handleDelete(id) {
      let apiURL = `http://localhost:4000/api-history/delete/${id}`;
            let indexOfArrayItem = this.histories.findIndex(i => i._id === id);
            if(window.confirm("Do you really want to delete?")){
                axios.delete(apiURL).then(() => {
                    this.histories.splice(indexOfArrayItem, 1)
                }).catch(error => {
                    console.log(error)
                })
            }
    }
  },
  created() {
    let apiURL = "http://localhost:4000/api-history";
    axios
      .get(apiURL)
      .then((res) => {
        this.histories = res.data;
        console.log(this.histories);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
.delete {
  border-radius:10px;
  padding:5px 10px;
  color:white;
  background:rgb(202, 61, 61);
  cursor:pointer;
}
.delete:hover{
  background:rgb(146, 44, 44);
}
table {
  border-spacing: 0;
  border: 2px solid rgb(61, 86, 226);
}

td {
  text-align: center;
  padding: 8px;
  border: 2px solid rgb(0, 0, 0);
}
tr {
  cursor: default;
}
tr:hover {
  background: #eee;
}

.ctn {
  background-color: #5F676E;
  width: 100%;
  height: 969px;
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
  background-color: #909CA6;
  cursor: default;
}
.blockheader:hover {
  background: #48b8d1;
}

.headerbutton {
  color: #111;
  padding: 20px 30px;
  font-size: 25px;
  border-radius: 15px;
  border: 1px solid #000;
}
button:hover {
  opacity: 0.5;
}
</style>