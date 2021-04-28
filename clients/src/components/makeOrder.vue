<template>
  <div class="ctn">
      <div class="header">
        <div class="leftheader">
          <p class="blockheader" >Shop</p>
        </div>
        <div class="rightheader">
          <router-link to="/"
            ><button
              class="headerbutton"
              style="background-color: #fdbca9; margin-left: 130px; color: #000"
            >
              Main Menu
            </button></router-link>

        </div>
      </div>
      <div class="Body">
        <div class="leftbody">
          <div
            style="
              margin: 20px;
              background-color: #facacb;
              width: 95%;
              height: 95%;
            "
          >
            <center>
              <pre> </pre>
              <div
                style="
                  border-radius: 25px;
                  height: 140px;
                  width: 70%;
                  background-color: #f5ebeb;
                  margin-top: 10px;
                "
              >
                <pre style="font-size: 1px"> </pre>
                <p style="margin-top: 10px; font-size: 30px" >Menu</p>
                <select
                  align="center"
                  style="
                    font-size: 18px;
                    background-color: #e7e2e3;
                    width: 350px;
                    height: 40px;
                  "
                  v-model="menu"
                  @click="clickmenu"
                >
                  <option value="เสื้อสเวตเตอร์คอกลมผู้ชาย ผ้าแฟลตนิต">เสื้อสเวตเตอร์คอกลมผู้ชาย ผ้าแฟลตนิต</option>
                  <option value="เสื้อยืดแขนสั้น ลายพิมพ์">เสื้อยืดแขนสั้น ลายพิมพ์</option>
                  <option value="เสื้อยืดลายกราฟิกผู้ชาย">เสื้อยืดลายกราฟิกผู้ชาย</option>
                  <option value="เสื้อยืดคอกลมผู้ชาย ปักสิงห์">เสื้อยืดคอกลมผู้ชาย ปักสิงห์</option>
                  <option value="เสื้อเชิ้ตแขนสั้นผู้ชาย พิมพ์ลาย">เสื้อเชิ้ตแขนสั้นผู้ชาย พิมพ์ลาย</option>
                  <option value="เสื้อเชิ้ตแขนสั้นผู้ชาย พิมพ์ลายทรอปิคอล">เสื้อเชิ้ตแขนสั้นผู้ชาย พิมพ์ลายทรอปิคอล</option>
                  <option value="เสื้อยืดลายกราฟิกผู้ชาย">เสื้อยืดลายกราฟิกผู้ชาย</option>
                  <option value="เสื้อยืดลายผู้ชาย_GOOD_GAME">เสื้อยืดลายผู้ชาย_GOOD_GAME</option>
                  <option value="เสื้อยืดลายกราฟิกผู้ชาย_HITHARD">เสื้อยืดลายกราฟิกผู้ชาย_HITHARD</option>
                  <option value="เสื้อยืดลายกราฟิกผู้ชาย_BASEBALL">เสื้อยืดลายกราฟิกผู้ชาย_BASEBALL</option>
                </select>
              </div>
               <br />
              

              <div
                style="
                  border-radius: 25px;
                  height: 140px;
                  width: 70%;
                  background-color: #f5ebeb;
                "
              >
                <pre style="font-size: 1px"> </pre>
                <p style="margin-top: 10px; font-size: 30px">Customer Name</p>
                <input type="text"
                  align="center"
                  style="
                    font-size: 18px;
                    background-color: #e7e2e3;
                    width: 350px;
                    height: 40px;
                  "
                  v-model="customer"
                >
              </div>
            </center>
          </div>
        </div>

        <div class="rightbody">
          <div
            style="
              margin: 20px;
              background-color: #facacb;
              width: 95%;
              height: 95%;
            "
          >
         <center> <p style="font-size:50px;font-weight: bold;">Preview</p>
          <div >
            <div style="width:393px;height:408px; background-color: rgba(0,0,0,0.1);">
              <img style="margin: 0 0 0 0;width:300px " :src="image">
            </div>
            
            </div>
            <div style="margin-top: 10px;"><p style="font-size:20px" >จำนวนสินค้าในคลัง : {{ quantity }}</p></div>
          <div style="margin-top: 20px;"><span  >{{ message }}</span></div>
          <div style="margin-top: 5px;"><span  >ราคา : {{ tmp }} บาท</span></div>
          <div v-show="btn" style="margin-top: 5px;"><span  >จำนวน</span> <input @click="totalprice" type="number" min=1 v-model="unitquantity" ></div>
          
          
          <button v-show="btn"  @click.prevent="handleSubmitForm" class="headerbutton" style="margin-top: 20px;padding: 15px 30px;font-size:20px;background-color:#fab3c3;color: #000;">Make Order</button>
          
          <button v-show="btn1"   class="btn-not" style="cursor:not-allowed;margin-top: 55px;padding: 15px 30px;font-size:20px;">Make Order</button>
            </center>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return {
      tmp: '0',
      btn : true,
      btn1 : false,
      image: '',
      customer:'Insert name',
      menu: 'เสื้อสเวตเตอร์คอกลมผู้ชาย ผ้าแฟลตนิต',
      size: 'L',
      message : '',
      price: 0,
      unitquantity : 1,
      product: {},
      history: {
        name: '',
        size: '',
        numberofunit: '',
        price: '',
        customer:''
      },
      quantity: null,

    }
  },
  created(){
        let apiURL = 'http://localhost:4000/api';
        axios.get(apiURL).then(res => {
            this.product = res.data
            console.log(this.product)
            // set app data
        }).catch(error => {
            console.log(error)
        })  
        
        
        
  },
  methods: {
    clickmenu(){
      for(var i in this.product){
      /*if(this.product[i].quantity == 0 && this.product[i].name === this.menu){
        this.btn = false
        this.btn1 = true
        break;
      }*/
      this.btn = true
      this.btn1 = false
    }
    },
    totalprice(){
      
      this.tmp = this.price
      this.tmp = this.tmp * this.unitquantity
    },
    async handleSubmitForm(){
      //console.log('++');
       // let r = confirm('ต้องการทำรายการนี้ ?')
       // if (r){
       for(let i = 0; i < this.product.length; i++){
          if (this.menu == this.product[i].name){
            this.product = this.product[i]

            //  update data
            /* let apiURL = `http://localhost:4000/api/update/${this.product._id}`;
            await axios.put(apiURL, this.product).then((res) => {
                console.log(res)
                //this.$router.push('/makeOrder')
            }).catch(error => {
                console.log(error)
            })*/

            // create history
             let apiURL = 'http://localhost:4000/api-history/create';
              await axios.post(apiURL, this.history).then(() => {
                this.history = {
                    name: '',
                    size: '',
                    numberofunit: '',
                    price: '',
                    customer: ''
                }
            }).catch(error => {
                console.log(error)
            })

            
            
          }
       }
       this.$router.go(this.$router.currentRoute)
     // }
    }
    
  },
  updated(){
    //console.log(this.product.length)


    this.history.customer = this.customer
    this.history.name = this.menu
    this.history.price = this.tmp
    this.history.numberofunit = this.unitquantity
    this.history.size = this.size
    //console.log( this.history.menu + " " + this.history.topping + " " + this.history.size +" " + this.history.numberofglass + " " + this.history.price)
    
/*
    if (this.size == 'S' && this.topping == 'ไม่ใส่') this.price = 20;
    else if (this.size == 'M' && this.topping == 'ไม่ใส่') this.price = 25;
    else if (this.size == 'L' && this.topping == 'ไม่ใส่') this.price = 30;
    else if (this.size == 'S' ) this.price = 25;
    else if (this.size == 'M' )  this.price = 30;
    else if (this.size == 'L' )  this.price = 35;
*/

      

    if (this.menu == 'เสื้อสเวตเตอร์คอกลมผู้ชาย ผ้าแฟลตนิต'){
          this.image = require('@/assets/img/makeorder/1.png')
          this.price = parseInt(this.product[0].price)
          this.size  = this.product[0].size
      }
      else if (this.menu == 'เสื้อยืดแขนสั้น ลายพิมพ์'){
          this.image = require('@/assets/img/makeorder/2.png')
          this.price = parseInt(this.product[1].price)
          this.size  = this.product[1].size
      }
       else if (this.menu == 'เสื้อยืดลายกราฟิกผู้ชาย'){
          this.image = require('@/assets/img/makeorder/3.png')
          this.price = parseInt(this.product[2].price)
          this.size  = this.product[2].size
      }
       else if (this.menu == 'เสื้อยืดคอกลมผู้ชาย ปักสิงห์'){
          this.image = require('@/assets/img/makeorder/4.png')
          this.price = parseInt(this.product[3].price)
          this.size  = this.product[3].size
      }
       else if (this.menu == 'เสื้อเชิ้ตแขนสั้นผู้ชาย พิมพ์ลาย'){
          this.image = require('@/assets/img/makeorder/5.png')
          this.price = parseInt(this.product[4].price)
          this.size  = this.product[4].size
      }
       else if (this.menu == 'เสื้อเชิ้ตแขนสั้นผู้ชาย พิมพ์ลายทรอปิคอล'){
          this.image = require('@/assets/img/makeorder/6.png')
          this.price = parseInt(this.product[5].price)
          this.size  = this.product[5].size
      }
       else if (this.menu == 'เสื้อยืดลายกราฟิกผู้ชาย'){
          this.image = require('@/assets/img/makeorder/7.png')
          this.price = parseInt(this.product[6].price)
          this.size  = this.product[6].size
      }
       else if (this.menu == 'เสื้อยืดลายผู้ชาย_GOOD_GAME'){
          this.image = require('@/assets/img/makeorder/8.png')
          this.price = parseInt(this.product[7].price)
          this.size  = this.product[7].size
      }
       else if (this.menu == 'เสื้อยืดลายกราฟิกผู้ชาย_HITHARD'){
          this.image = require('@/assets/img/makeorder/9.png')
          this.price = parseInt(this.product[8].price)
          this.size  = this.product[8].size
      }
       else if (this.menu == 'เสื้อยืดลายกราฟิกผู้ชาย_BASEBALL'){
          this.image = require('@/assets/img/makeorder/10.png')
          this.price = parseInt(this.product[9].price)
          this.size  = this.product[9].size
      }
    this.message = this.history.menu +', Size : '+ this.history.size + this.history.customer + this.history.price + this.history.numberofunit
  }

}
</script>

<style scoped>
.btn-not {
  background-color: rgb(202, 38, 38);
  color: rgb(255, 255, 255);
  padding: 20px 30px;
  font-size: 25px;
  border-radius: 15px;
  border: 5px solid rgb(124, 122, 122);
}
.btn-not:hover {
  opacity: 1;
}
select {
  cursor: pointer;
}
p {
  cursor:default;
}
button:hover {
  opacity: 0.5;
}

span {
  font-size: 25px;
  background-color:rgb(240, 234, 234);
  cursor:default;
}
.ctn {
  background-color: #ffffff;
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
  height: 819px;
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
.leftbody {
  width: 50%;
  height: 100%;
  float: left;
}

.rightbody {
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
  background-color: #f79b8f;
}
.blockheader:hover {
  background-color: #d1857b;
}

.headerbutton {
  color: aliceblue;
  padding: 20px 30px;
  font-size: 25px;
  border-radius: 15px;
  border: 1px solid #000;
}

</style>