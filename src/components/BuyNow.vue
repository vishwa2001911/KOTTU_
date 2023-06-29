<template>
    <div class="buy">
        
        <div class="buybox">
            <form>
            <h1 class="buyTitle">Personal Infprmation</h1>
            <label for="">Name and Surname</label>
            <input type="text" class="inputName" placeholder="Full Name">
            <label for="">Address</label>
            <input type="text" class="inputAddress" placeholder="D.R. Wijewardena Mawatha Colombo 10">
            <h1 class="buyTitle">Card Information</h1>
            <input type="text" class="inputCardNum"  placeholder="Card Number">
            <div class="card">
                <input type="text" class="cardINfo" placeholder="Month">
                <input type="text" class="cardINfo" placeholder="Year">
                <input type="text" class="cardINfo" placeholder="CVV">
            </div>
            <div class="btnbox">
                <button class="check" @click.prevent="Checkout()">Checkout..</button>
            </div>
            </form>
            <div class="products">
                <h1 class="productTitle">Review item</h1>

                <ul class="buyulItems">

                    
                        <li class="buyliitem" v-for="(item, index) in pickedItems" :key="index" >
                            <h4 class="buyItemName">{{ item.name }}</h4>
                            <h4 class="buyItemPrice">${{ item.price }}</h4>
                            <h4 class="numOfItems">{{ item.numberOfItems }}x</h4>
                            <div class="addORremove">
                                <button class="add" @click="addItem(index)">+</button>
                                <button class="add" @click="subItem(index)" style="padding: 1px 8px;">-</button>
                            </div>
                        </li>
                    


                    <li class="totle">
                        
                        <h4 >Totle Price:- ${{ total.toFixed(2) }}</h4>
                    </li>
                </ul>
            </div>
            <span class="closeBtn" @click="closebtn()">X</span>
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
            total:0
        }
    },
    beforeMount() {
        this.calculate()
        
        
    },

    methods: {
        calculate(){
            let count = 0

            this.pickedItems.forEach((i) => {
                count = count + (i.numberOfItems * i.price)
            });

            this.total = count

        },
        addItem(index){
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
        }},
        Checkout(){
            this.$emit('checkout')
        },
        closebtn(){
            this.pickedItems.length = 0;
            this.$emit('closebtn')
        }
    },

}
</script>

<style>

.closeBtn{
    position: absolute;
    top: 20px;
    right: 20px;
    font-weight: bolder;
    cursor: pointer;
    color: lightgray;
}

.btnbox{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 30px;
}

.check{
    width: 50%;
    height:30px;
    background: lightgray;
    border: none;
    outline: none;
    border-radius: 10px;
    cursor: pointer;
    color:#2c3e50;
    font-weight: bold;
    transition: 0.4s;
    font-size: 17px;
}

.check:hover{
    background: greenyellow;
}

.add{
    padding: 1px 6px;
    background-color: #2c3e50;
    border: none;
    border-radius: 5px;
    color: whitesmoke;
    font-weight: bold;
    margin-left: 5px;
    cursor: pointer;
    font-size: 20px;
    transition: 0.4s;

}

.add:hover{

    background-color: red;


}

.buyliitem{
    display: flex;
    align-items: center;
    justify-content:space-between;
    width: 500px;
    height:40px;
    background: lightgray;
    border: none;
    outline: none;
    padding: 0 20px;
    border-radius: 10px;
}

.totle{
    display: flex;
    text-align: center;
    justify-content: center;
    align-items: center;
    width: 500px;
    height:30px;
    background: lightgray;
    border: none;
    outline: none;
    border-radius: 10px;
}

.buyulItems{
    width: 100%;
    display: flex;
    align-items: center;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 30px;
    position: relative;
}

.products{
    display: flex;
    flex-direction: column;
    gap: 40px;
}

.card{
    display: flex;
    gap: 10px;
    margin-top: 10px;
}

.inputName, .inputAddress, .inputCardNum, .cardINfo {
    width: 100%;
    height:30px;
    background: lightgray;
    border: none;
    outline: none;
    border-radius: 10px;
    text-align: center;

}




.buy{
    position: fixed;
    width: 100vw;
    height: 100vh;
    background-image: url('https://images.pexels.com/photos/1583884/pexels-photo-1583884.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1');
    top: 0;
    background-size: cover;
    background-repeat: no-repeat;
    left: 0;
    z-index: 3;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px;
}



.buybox{
    width: 50%;
    background-color: azure;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 300px;
    gap: 30px;
    position: relative;
    border-radius: 10px;
    -webkit-box-shadow: 10px 10px 5px -8px rgba(57,57,122,0.6);
-moz-box-shadow: 10px 10px 5px -8px rgba(57,57,122,0.6);
box-shadow: 10px 10px 5px -8px rgba(57,57,122,0.6);
}

form{
    display: flex;
    flex-direction: column;
    gap: 5px;
    padding: 30px;
}

.buyItemPrice{
    position: absolute;
    right: 150px;
}

.numOfItems{
    position: absolute;
    right: 80px;
}

@media screen and (max-width: 1271px) {
    .buybox{
        width: 60%;
        margin-top: 80px;
        gap: 0;
    }
}

@media screen and (max-width: 867px) {
    .buy{
    width: 100vw;
    height: 100vh;
    padding: 0px;
}
    .buybox{
        width: 80%;
        margin-top: 80px;
    }

}

@media screen and (max-width: 867px) {
    .buy{
    width: 100vw;
    height: 100vh;
    padding: 0px;
}
    .buybox{
        width: 80%;
        margin-top: 80px;
    }

}

@media screen and (max-width: 659px) {

    .buybox{
        width: 90%;
        margin-top: 60px;
    }

    .products{
        text-align: center;
    }

    .buyliitem,.totle{
        width: 85vw;
        font-size: 13px;
    }
    .buyItemPrice{
        right: 135px;
    }

    .numOfItems{
        right: 95px;
    }
}

</style>