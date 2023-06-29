<template>
  <div class="cart-container">
     <div class="cart-box">
        <div class="cart-in-box1">
          <span class='getItemsNow' v-if="pickedItems.length == 0">
            <h1>Please Choose your items</h1>
            <img src="https://www.iconpacks.net/icons/2/free-shopping-cart-icon-2029-thumb.png" style="max-width: 200px;" alt="">
          </span>
          <ul v-if="pickedItems.length != 0">
            <li class="cart-li">
            <h6 class="cartName" style="font-size: 15px;">ITEM  </h6>
            <h6 class="cartItemPrice" style="font-size: 15px;">PRICE </h6>
            <h6 class="catrQTY" style="font-size: 15px; margin-left: 10px;">QTY</h6>
            <h6 class="totalItems" style="font-size: 15px;">TOTAL </h6>
            </li>
          </ul>
          <ul class="cart-ul" v-if="pickedItems.length != 0">

            <li class="cart-li" v-for="(item, index) in pickedItems" :key="index">
              <h5 class="cartName" style="font-size: 14px; font-weight: bold;">{{ item.name }}</h5>
              <h6 class="cartItemPrice" style="font-size: 15px;">${{ item.price }}</h6>
              <div class="catrQTY">
                <span class="Cartadd" @click="clickCount(index)">
                  <svg  xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-plus-lg" viewBox="0 0 16 16">
                    <path fill-rule="evenodd" d="M8 2a.5.5 0 0 1 .5.5v5h5a.5.5 0 0 1 0 1h-5v5a.5.5 0 0 1-1 0v-5h-5a.5.5 0 0 1 0-1h5v-5A.5.5 0 0 1 8 2Z"/>
                  </svg>
                </span>
                <span class="CartQTY_Number">{{ item.numberOfItems }}</span>
                <span class="Cartadd" style="margin-bottom: 10px;" @click="subItem(index)">
                  <svg  xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-dash" viewBox="0 0 16 16">
                    <path d="M4 8a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7A.5.5 0 0 1 4 8z"/>
                  </svg>
                </span>
              </div>
              <h6 class="totalItems" style="font-size: 15px;">{{ item.numberOfItems * item.price}}</h6>
            </li>

          </ul>
        </div>
        <div class="cart-in-box2">
            <div class="checkOutBox">
              <h4 >Cart Total <span> ${{ total }}</span></h4>
              <h6>Shopping & Taxes Calculated at Checkout</h6>
              <span style="font-size: 10px; display: flex; align-items: center;">
                <input type="checkbox" name="Agree" id="agree">    I agree to <a href="" style="color: blue; text-decoration: none;">Terms and Conditions</a>
              </span>
              <button class="cart_Checkout_btn" @click.prevent="Checkout()">
                CHECKOUT 

                <svg xmlns="http://www.w3.org/2000/svg" width="15px" height="15px" fill="currentColor" class="bi bi-bag" viewBox="0 0 16 16">
                  <path d="M8 1a2.5 2.5 0 0 1 2.5 2.5V4h-5v-.5A2.5 2.5 0 0 1 8 1zm3.5 3v-.5a3.5 3.5 0 1 0-7 0V4H1v10a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V4h-3.5zM2 5h12v9a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V5z"/>
                </svg>
              </button>
            </div>
            <div class="cartCloseBox" @click="ClickCartClose()">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-x-lg" viewBox="0 0 16 16">
               <path d="M2.146 2.854a.5.5 0 1 1 .708-.708L8 7.293l5.146-5.147a.5.5 0 0 1 .708.708L8.707 8l5.147 5.146a.5.5 0 0 1-.708.708L8 8.707l-5.146 5.147a.5.5 0 0 1-.708-.708L7.293 8 2.146 2.854Z"/>
            </svg>
            </div>
        </div>
     </div>
     <span class="cartHeader">
      <img src="" alt="" class="cartHeaderImg" style="width: 100px;">
     </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      total:0
    }
  },
  props:[
    'pickedItems',
    'menuItems',
    'icount'
  ],
methods: {
  Checkout(){
    this.$emit('Click_checkout_btn')
    
  },
  ClickCartClose(){

    /*
    this.menuItems.forEach((i)=>{
      i.count = 0;
    })
    */
    this.pickedItems.length = 0

    this.menuItems.map((i)=>{
        i.count = 0
    })

    
    
    this.$emit('ClickCartClose')
  },
  calculate(){
            let count = 0

            this.pickedItems.forEach((i) => {
                count = count + (i.numberOfItems * i.price)
            });

            this.total = count.toFixed(2)

  },
  clickCount(index){
            this.pickedItems[index].numberOfItems++;
            this.calculate();
        },
        subItem(index){
            if(this.pickedItems[index].numberOfItems > 0){
                this.pickedItems[index].numberOfItems--;
                this.calculate();
            if(this.pickedItems[index].numberOfItems === 0){
                this.pickedItems.splice(index, 1)
            }
        }}
},
mounted() {
  this.calculate();
},
}
</script>

<style>


.cartCloseBox{
  position: absolute;
  top: 10px;
  right: 10px;
  color: black;
  cursor: pointer;
}

.cartHeader{
  display: none;
}


::-webkit-scrollbar{
  width: 10px;
  height: 40px;
}
::-webkit-scrollbar-thumb{
  background-color: rgb(248, 220, 243);
  height: 40px;
}

.cart-ul{
  height: 300px;

}



.Cartadd{
  cursor: pointer;
}



.catrQTY{
  display: flex;
  justify-content: center;
  align-items: baseline;
  gap: 5px;
}

.cartName{
  position: absolute;
  left: 0;
  
}

.cartItemPrice{
  position: absolute;
  left: 250px;
  font-weight: bold;
  
}

.catrQTY{
  position: absolute;
  left: 350px; 
}

.totalItems{
  position: absolute;
  left: 430px;
}

.cart-li{
  position: relative;
  display: flex;
  width: 500px;
  height: 60px;
  padding: 10px;
}

.checkOutBox{
  display: flex;
  flex-direction: column;
  justify-content:center;
  gap: 20px;
  align-items: center;
  
}

.cart_Checkout_btn{
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 150px;
  padding: 5px;
  border-radius: 10px;
  background-color: black;
  color: whitesmoke;
  font-size: 15px;
  cursor: pointer;
  transition: 0.4s;
}

.cart_Checkout_btn:hover{
  background-color: lightgray;
  color: black;

}

.cart-in-box1{
  width: 70%;
  min-height: 500px;
  background-color:white;
  display: flex;
  flex-direction: column;
  justify-content:flex-start;
  padding-top: 50px;
  align-items:center;
  
}

.getItemsNow{
  margin-top: 100px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.cart-in-box2{
  width: 30%;
  min-height: 500px;
  /*background-color: rgb(248, 220, 243); 
  background-image: url('https://images.unsplash.com/photo-1571456653714-a8db063a3e91?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80');
  background-repeat: no-repeat;
  background-size: cover;
  */
  background-color: yellow;
  display: flex;
  flex-direction: column;
  justify-content:center;
  align-items: center;
  position: relative;
}

.cart-box{
  width: 60%;
  min-height: 500px;
  background-color: white;
  display: flex;


}

.cart-container{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    z-index: 3;
    background-color:lightgray;
    background-image: url('https://cdn.wallpapersafari.com/48/9/6PRMV8.jpg');
    background-repeat: no-repeat;
    background-size: cover;
}

.cartItem{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

@media screen and (max-width: 900px) {
  .cart-in-box2{
  width: 100vw;
  min-height: 300px;
  position: absolute;
  bottom: 0;
  left: 0;
  border-top-left-radius: 30px;
  border-top-right-radius: 30px;
  z-index: 3;
  -webkit-box-shadow: 1px 1px 11px -2px rgba(0,0,0,0.75);
-moz-box-shadow: 1px 1px 11px -2px rgba(0,0,0,0.75);
box-shadow: 1px 1px 11px -2px rgba(0,0,0,0.75);
}

.cart-in-box1{
  width: 100vw;
  min-height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  overflow: hidden;
  overflow-y: scroll;
}

.cart_Checkout_btn{
  display: flex;
  justify-content: center;
  gap: 10px;
  width: 250px;
  padding: 10px;
  border-radius: 10px;
  background-color: black; 
  border: none;
}

.cartCloseBox{
  position: absolute;
  top: 15px;
  right: 20px;
  color: black;
  cursor: pointer;
}

.cart-li{
  width: 100vw;
}
.cartName{
  left: 16px;
  width: 130px;
}
.cartItemPrice{
  left: 150px;
}
.catrQTY{
  left: 227px;
}
.totalItems{
  left: 300px;
}

.cartHeader{
  display: block;
  position: absolute;
  top: 0;
  width: 100vw;
  left: 0;
  background-color: yellow;
  height: 30px;
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
  -webkit-box-shadow: 1px 1px 11px -2px rgba(0,0,0,0.75);
-moz-box-shadow: 1px 1px 11px -2px rgba(0,0,0,0.75);
box-shadow: 1px 1px 11px -2px rgba(0,0,0,0.75);
}


}


</style>