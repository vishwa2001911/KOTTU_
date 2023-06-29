<template>

  <NavBar  v-if="!isClicked || !isCartClose" :pickedItems="iCount" @clickCart="ClickCartClose()"></NavBar>
  <Header  v-if="!isClicked || !isCartClose" ></Header>
  <TodaysOffer  v-if="!isClicked || !isCartClose" :pickedItems="pickedItems" @BuyNowClicked="clicked()"  @clickCart="ClickCartClose()" > </TodaysOffer>
  <menuItems v-if="!isClicked || !isCartClose"  :menuItems="menuItems" :pickedItems="pickedItems" @clickCart="ClickCartClose()"  @addItems="addItems" ></menuItems> 
  <About v-if="!isClicked || !isCartClose"></About>
  <BuyNow :pickedItems="pickedItems" @closebtn="clicked()"  @checkout="checkout()" v-if="isClicked"></BuyNow>
  <cart @ClickCartClose="ClickCartClose"  :icount="iCount" :pickedItems="pickedItems" :menuItems="menuItems"  @Click_checkout_btn="checkedClicked()" v-if="isCartClose" ></cart>


</template>

<script>
import NavBar from './components/NavBar.vue'
import Header from './components/Header.vue'
import TodaysOffer from './components/TodaysOffer.vue'
import menuItems from './components/menuItems.vue'
import About from './components/About.vue'
import BuyNow from './components/BuyNow.vue'
import cart from './components/cart.vue'


export default {
  data() {
    return {
      menuItems:[
                {
                    itemName:'Chicken Kottu',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:false
                },
                {
                    itemName:'Chicken Fried Rice',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:true
                },
                {
                    itemName:'Cheese and Crab Kottu',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:true
                },
                {
                    itemName:'Lamp Rice',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:true
                },
                {
                    itemName:'Chicken Kottu',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:false
                },
                {
                    itemName:'Chiken Kottu',
                    price:3.56,
                    image:"url",
                    ratings:4.9,
                    count:0,
                    oldPrice:4.99,
                    offer:false
                },
                {
                    itemName:'Chiken Kottu',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:false
                },
                {
                    itemName:'Chiken Kottu',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:true
                },
                {
                    itemName:'Chiken Kottu',
                    price:3.56,
                    image:"url",
                    ratings:'4.9',
                    count:0,
                    oldPrice:4.99,
                    offer:true
                },
            ],
            pickedItems:[],
            isClicked:false,
            isCartClose:false,
            iCount:0
    }
  },
  methods: {
    checkedClicked(){
          this.isCartClose=false
          this.isClicked = true
    },
    addItems(i){
      this.iCount = i
    },
    clicked(){
      this.isClicked = !this.isClicked 
    },
    checkout(){
      this.clicked();
      alert("Your items will arive with in 35 minuts")
    },
    ClickCartClose(){
      this.isCartClose = !this.isCartClose
      this.iCount = 0;
      this.menuItems.forEach((i,index)=>{
      if(i.count!=0){
          this.pickedItems.push(
              {
              name:this.menuItems[index].itemName,
              price:this.menuItems[index].price,
              numberOfItems:this.menuItems[index].count        
          }
      )
      }
      })
    }
  },
  name: 'App',
  components: {
    NavBar,
    Header,
    TodaysOffer,
    menuItems,
    About,
    BuyNow,
    cart

  },
  
}
</script>

<style>

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  overflow-x: hidden;
}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
}
</style>
