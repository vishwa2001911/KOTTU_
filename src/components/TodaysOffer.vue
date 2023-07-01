<template>
<div class="todaysoffer">
    <div class="slider">
        <div class="sliderBox" id="sliderBox">

            <div v-for="(item, index) in offerItems" :key="index">
                <div class="sliderItem" >
                
                <img :src="item.image" alt="" class="sliderImg">
                
                <div class="sbox">
                    <div class="extraDetail">
                            <div>
                                <span style="color: yellow;" :class="{ ye: item.ratings>=1 && item.ratings<=2 }" class="fa fa-star checked"></span>
                                <span style="color: yellow;" :class="{ ye: item.ratings>=2 && item.ratings<=3 }" class="fa fa-star checked"></span>
                                <span style="color: yellow;" :class="{ ye: item.ratings>=3 && item.ratings<=4 }" class="fa fa-star checked"></span>
                                <span class="fa fa-star" :class="{ ye: item.ratings>=4 && item.ratings<=5 }" > </span>
                                <span class="fa fa-star" :class="{ ye: item.ratings>=5 }"></span>
                            </div>
                            <h4>{{ item.ratings }}</h4>
                    </div>
                    <h1 class="sliderItemTitle">{{ item.name}}</h1>
                    <div class="price">
                        
                        <h3 class="priceAfter">Price: <span  class="priceBefor">${{item.price.befroPrice}}</span> <span style="color: red;">${{item.price.afterPrice }}</span></h3>
                    </div>
                    <div class="buttons">
                        <a class="buynow" @click="clickCount(index)">Buy Now..</a>
<!--
    
-->
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
            isActive:true,
            offerItems:[
                {
                    name:"Cheese & Chicken Kottu",
                    price:{
                        befroPrice:3.4,
                        afterPrice:2.5,
                    },
                    ratings:3.9,
                    image:'https://github.com/vishwa2001911/KOTTU_/blob/master/src/assets/img/img/Veg-Cheese-Kottu.png?raw=true'
                },
                {
                    name:"Chicken Fried Rice",
                    price:{
                        befroPrice:4.5,
                        afterPrice:3.3,
                    },
                    ratings:4.9,
                    image:'https://github.com/vishwa2001911/KOTTU_/blob/master/src/assets/img/img/Chicken-Fried-Rice_.png?raw=true'
                },
                {
                    name:"Cheese Noodls",
                    price:{
                        befroPrice:5.4,
                        afterPrice:4.2,
                    },
                    ratings:5,
                    image:'https://github.com/vishwa2001911/KOTTU_/blob/master/src/assets/img/img/Cheese-Ramen-Noodles.png?raw=true'
                },
                {
                    name:"Lamprice",
                    price:{
                        befroPrice:4.99,
                        afterPrice:3.99,
                    },
                    ratings:4.6,
                    image:'https://github.com/vishwa2001911/KOTTU_/blob/master/src/assets/img/img/lamprais-.png?raw=true'
                },
                {
                    name:"Mutton Biriyani",
                    price:{
                        befroPrice:5.99,
                        afterPrice:4.99,
                    },
                    ratings:4.8,
                    image:'https://github.com/vishwa2001911/KOTTU_/blob/master/src/assets/img/img/mutton-fried-rice.png?raw=true'
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

.ye{
    color: yellow;
}

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
    gap: 15px;
    width: 100%;
    align-items: center;
    margin: 50px 0 ;
    margin-top: 10px;
    flex-wrap: wrap;
}

.sliderli{
    list-style: none;
    border: none;
    padding: 5px 15px;
    background-color: #2c3e50;
    border-radius: 17px;
    color: whitesmoke;
    font-size: 15px;
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
    padding: 10px 20px;
    background-color: yellow;
    border: solid black 3px;
    font-weight: bold;
    color: black;
    font-size: 20px;
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
    color: black;
    border-color: orange;
    background-color: orange;
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

@media screen and (max-width: 374px) {

    .sliderItemTitle{
        width: 70%;
        text-align: center;
    }
}


</style>