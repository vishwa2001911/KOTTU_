<template>

<h1 class="MenuBoxTitle">Our Menu</h1>
<div class="MenuItemsBox">
    

    <div class="MenuItems">

           
                <div class="MenuBox" v-for="(item, index) in menuItems" :key="index">

                    <img src="../assets/Chicken-Kottu-removebg-preview.png" alt="" class="menuItemIMG">
                    <h1 class="itemName">{{ item.itemName }}</h1>
                    <div class="rate-stars">
                        <span style="color: yellow;" class="fa fa-star checked"></span>
                        <span style="margin-left: 10px;">{{ item.ratings }}</span>
                    </div>
                    <h4 class="ItemPrice">{{ item.price }}</h4>

                    <span class="numberCount" v-if="item.count!=0">{{ item.count }}</span>

                    <button class="MenuBtn" @click="clickCart()">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-cart-fill" viewBox="0 0 16 16">
                            <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
                        </svg>
                    </button>
                    <button class="count" @click="clickCountSUB(index)" >-</button>
                    <button class="sub" @click="clickCount(index)" >+</button>
                </div>
           
    </div>




</div>
</template>

<script>
export default {
    props:[
        'menuItems',
        'pickedItems'
    ],
    data() {
        return {
            number:0,
            itemCount:0
            
        }
    },
    methods:{
        clickCount(index){
            
            this.menuItems[index].count++;
            this.itemCount++;

            this.$emit('addItems',this.itemCount)
            /*
            let obj = {
                    name:this.menuItems[index].itemName,
                    price:this.menuItems[index].price,
                    numberOfItems:this.menuItems[index].count
                
            }

            if (`${index}` in this.itemCount){
                console.log(this.pickedItems)
                this.itemCount.push(`${index}`)
            }else{
                this.pickedItems.push(obj)
            }
            */

            
            console.log(this.pickedItems)
            
        },
        clickCountSUB(index){
            if(this.menuItems[index].count>0 && this.itemCount>0){
                this.menuItems[index].count--;
                this.itemCount--;
                this.$emit('addItems',this.itemCount)
            }
            /*if ( this.menuItems[index].count > 0){
                this.menuItems[index].count--;

                this.pickedItems.pop()
            } */
            
        },
        clickCart(){
            this.$emit('clickCart')
        }
            
        },
        onMounted() {
        if (this.pickedItems.length == 0) {
            menuItems.forEach((i)=>{
                i.count = 0;
            })
        }

        
    },
    

    unmounted() {

        /*
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
        */
    },

    }


</script>

<style>


.numberCount{
    font-size: 20px;
    position: absolute;
    font-size: 13px;
    cursor: pointer;
    top: 0;
    right: 3px;
    z-index: 1;
    padding: 3px 5px;
    border-radius: 50%;
    background-color: yellow;
    font-weight: bold;
}

.rate-stars{
    position: absolute;
    bottom: 41px;
    font-weight: bolder;
    left: 130px;
    font-size: 15px;
}

.ItemPrice{
    position: absolute;
    bottom: 14px;
    font-weight: bolder;
    left: 130px;
    font-size: 20px;
}


.itemName{
    position: absolute;
    top: 79px;
    left: 122px;
    font-size: 20px;
}



.menuItemIMG{
    
    position:absolute;
    top: -15px;
    left: -34px;
    width: 200px;
    -webkit-filter: drop-shadow(5px 5px 5px #222);
  filter: drop-shadow(3px 5px 7px #bfb0bf);
}


.count{
    background-color: #2c3e50;
    padding: 5px 13px;
    position: absolute;
    border: none;
    border-radius: 10px;
    color: white;
    bottom: 10px;
    font-weight: bold;
    font-size: 20px;
    right: 5px;  
    -webkit-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    -moz-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    cursor: pointer;
    transition: 0.4s;
}

.sub{
    background-color: #2c3e50;
    padding: 5px 10px;
    position: absolute;
    border: none;
    border-radius: 10px;
    color: white;
    bottom: 10px;
    font-weight: bold;
    font-size: 20px;
    right: 45px;  
    -webkit-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    -moz-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    cursor: pointer;
    transition: 0.4s;
}

.count:hover{
    -webkit-box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
    -moz-box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
    box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
}

.MenuItemsBox{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    overflow: visible;
    padding: 20px;
}

.MenuBoxTitle{
    text-align: center;
    margin: 50px;
    font-size: 80px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.MenuBtn{
    background-color: red;
    padding: 10px;
    position: absolute;
    border: none;
    border-radius: 50%;
    color: white;
    top: 5px;
    right: 5px;
    -webkit-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    -moz-box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    box-shadow: 6px 5px 5px -3px rgba(191,176,191,1);
    cursor: pointer;
    transition: 0.4s
}

.MenuBtn:hover{
    -webkit-box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
    -moz-box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
    box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
}

.MenuBox{
    width: 300px;
    border: solid whitesmoke 2px;
    border-radius: 20px;
    background-color: whitesmoke;
 
    display: flex;
    flex-direction: column;
    height: 200px;
    position: relative;
    -webkit-box-shadow: 7px 9px 7px -3px rgba(191,176,191,1);
    -moz-box-shadow: 7px 9px 7px -3px rgba(191,176,191,1);
    box-shadow: 7px 9px 7px -3px rgba(191,176,191,1);
    transition: 0.4s;
    margin: 10px;
  
}

.MenuBox:hover{
    -webkit-box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
-moz-box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
box-shadow: 6px 5px 5px 0px rgba(191,176,191,1);
}

.MenuItems{
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    align-items: center;
    justify-content:center;
    margin: 50px;
}

.MenuItemsBox{
    background-color: #EBEDEF;
    clip-path: polygon(0 4%, 100% 0, 100% 100%, 0% 100%);
}


@media screen and (max-width: 475px) {
    .MenuItems{
        margin: 50px 5px;
    }
    .MenuBox{
        width: 100%;
    }
}
</style>