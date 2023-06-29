<template>
<div class="todaysoffer">
    <div class="slider">
        <div class="sliderBox" id="sliderBox">

            <div v-for="(item, index) in offerItems" :key="index">
                <div class="sliderItem" >
                
                <img src="../assets/img/Chicken-Fried-Rice__1_-removebg-preview.png" alt="" class="sliderImg">
                
                <div class="sbox">
                    <div class="extraDetail">
                            <div>
                                <span style="color: yellow;" class="fa fa-star checked"></span>
                                <span style="color: yellow;" class="fa fa-star checked"></span>
                                <span style="color: yellow;" class="fa fa-star checked"></span>
                                <span class="fa fa-star"></span>
                                <span class="fa fa-star"></span>
                            </div>
                            <h4>{{ item.ratings }}</h4>
                    </div>
                    <h1 class="sliderItemTitle">{{ item.name}}</h1>
                    <div class="price">
                        
                        <h3 class="priceAfter">Price: <span  class="priceBefor">${{item.price.befroPrice}}</span> <span style="color: red;">${{item.price.afterPrice }}</span></h3>
                    </div>
                    <div class="buttons">
                        <a class="buynow" @click="clickCount(index)">Buy Now..</a>
                        <a href="" class="cart" @click.prevent="clickCart()">
                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-cart-fill" viewBox="0 0 16 16">
                            <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
                            </svg>
                        </a>
                    </div>
                </div>
            
        </div>
            </div>
        </div>

        <ul class="sliderul">
            <li class="sliderli" @click="liClicked(index)"  v-for="(item, index) in offerItems" :key="index">
                {{ item.name }}
            </li>
        </ul>
    </div>
</div>
</template>

<script>
export default {
    props:[
        'pickedItems'
    ],
    data() {
        return {
            offerItems:[
                {
                    name:"Chees & Crab Kottu",
                    price:{
                        befroPrice:3.4,
                        afterPrice:2.5,
                    },
                    ratings:5,
                    image:'../assets/2-removebg-preview.png'
                },
                {
                    name:"Chicken Fried Rice",
                    price:{
                        befroPrice:4.5,
                        afterPrice:3.3,
                    },
                    ratings:4.9,
                    image:'../assets/2-removebg-preview.png'
                },
                {
                    name:"Kottu",
                    price:{
                        befroPrice:5.4,
                        afterPrice:4.2,
                    },
                    ratings:5,
                    image:'../assets/2-removebg-preview.png'
                },
                {
                    name:"Kottu",
                    price:{
                        befroPrice:4.99,
                        afterPrice:3.99,
                    },
                    ratings:5,
                    image:'../assets/2-removebg-preview.png'
                },
                {
                    name:"Kottu",
                    price:{
                        befroPrice:5.99,
                        afterPrice:4.99,
                    },
                    ratings:5,
                    image:'../assets/2-removebg-preview.png'
                },
            ],
            isBuyNowClicked:false
        }
    },
    methods: {
        liClicked(index){
            const slider = document.getElementById("sliderBox");

            slider.style.transform = `translateX(${-100 * index}vw)`
        },
        clickCount(index){
            this.pickedItems.push({
                    name:this.offerItems[index].name,
                    price:this.offerItems[index].price.afterPrice,
                    numberOfItems:1
            })
            this.isBuyNowClicked = !this.isBuyNowClicked

            this.$emit('BuyNowClicked')
            
        },
        clickCart(){
            this.$emit('clickCart')
        }
    },

}
</script>

<style>

.price{
    display: flex;
    gap: 20px;
}

.priceBefor{
    text-decoration:line-through;
}

.extraDetail{
    display: flex;
    gap: 20px;
}


.sliderul{
    display: flex;
    justify-content: center;
    gap: 50px;
    width: 100%;
    align-items: center;
    margin: 50px 0;
    flex-wrap: wrap;
}

.sliderli{
    list-style: none;
    font-size: 20px;
    font-weight: bolder;
    cursor: pointer;
    transition: 0.4s;
}

.sliderli:hover{
    color: black;
}

.sbox{
    width: 500px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    margin-top: 30px;
    
}


.buynow{
    padding: 5px 10px;
    background-color: yellow;
    border: solid yellow 2px;
    font-weight: bold;
    color: grey;
    border-radius: 8px;
    text-decoration: none;
    cursor: pointer;
    text-align: center;
    transition: 0.4s;
}

.cart{
    padding: 5px 10px;
    background-color:red;
    border: none;
    font-weight: bold;
    color: whitesmoke;
    border-radius: 8px;
    text-decoration: none;
    cursor: pointer;
    text-align: center;
    transition: 0.4s;
}

.cart:hover{
    -webkit-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    -moz-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
}

.buynow:hover{
    background-color: transparent;
    color: yellow;
}



.sliderItem{
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
}

.sliderItemTitle{
    font-size: 70px;
}

.extraDetail{

    font-size: 30px; 
}

.buttons{
    width: 160px;
    display: flex;
    justify-content: space-between;

}


.sliderImg{
    width: 50%;
    -webkit-filter: drop-shadow(5px 5px 5px #222);
  filter: drop-shadow(3px 5px 7px #bfb0bf);
}

.todaysoffer{
    width: 100%;
    overflow-x: hidden;
}

.slider{
    clip-path: polygon(0 3%, 100% 0, 100% 100%, 0 96%);
    background: #EBEDEF;
}

.sliderBox{
    width: 500vw;
    display: flex;
    transition: all 0.7s ease-in-out;
    
}

.shape{
    z-index: -1;
    position: absolute;
    top: 50px;
}

@media screen and (max-width: 655px) {
    .sliderItem{
        padding-top: 20px;
        flex-direction: column;
    }

    .sliderImg{
        width: 80%;
    }

    .sliderItemTitle{
        width: 90%;
        text-align: center;
    }
}


</style>