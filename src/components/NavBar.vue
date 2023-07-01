<template>
  <nav>
    <div class="pc">
        <img class="logo" src="https://github.com/vishwa2001911/Project_/blob/master/img/Yellow%20Abstract%20Cooking%20Fire%20Free%20Logo%20(1).png?raw=true" style="width: 80px; position: absolute; top: 0; left: 30px;">
        <a class="Navoffer">
            Todays Offer
        </a>
        <button class="MenuBtn2"  @click="clickCart()">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-cart-fill" viewBox="0 0 16 16">
                <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
            </svg>
        </button>
        <!--
            <span class="numberCount" style="color: #2c3e50; top: 16px; right: 20px;">{{ pickedItems }}</span>
        -->
    </div>



  </nav>
</template>

<script>
export default {
    data() {
        return {
        }
    },
    props:[
        'pickedItems'
    ],
    methods: {
        clickCart(){
            this.$emit('clickCart')
        }
    },



}
</script>

<style>



.MenuBtn2{
    background-color: red;
    padding: 10px;
    position: absolute;
    border: none;
    border-radius: 50%;
    color: white;
    top: 23px;
    right: 25px;

    cursor: pointer;
    transition: 0.4s
}


nav{
    height: 80px;
    width: 100%;
    position:fixed;
    background-color: black;
    top: 0;
    left: 0;
    z-index: 2;
    -webkit-box-shadow: 2px 2px 5px 1px rgba(15,13,15,0.46);
    -moz-box-shadow: 2px 2px 5px 1px rgba(15,13,15,0.46);
    box-shadow: 2px 2px 5px 1px rgba(15,13,15,0.46);
    z-index: 2;
}



.Navoffer{
    font-size: 20px;
    font-weight: 700;
    border-bottom: solid green 2px;
    text-decoration: none;
    z-index: 2;
    cursor: pointer;
}


.pc{
    display: flex;
    align-content: center;
    justify-content: space-around;
    padding-top: 30px;
    padding-bottom: 0;
    z-index: 2;
    color: whitesmoke;
    
}

@media screen and (max-width: 500px) {
    .Navoffer{
        display: none;
    }
}




</style>