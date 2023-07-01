<template>
  <header>
    <div class="headerBox">
        <h1 class="HeaderTitle">MEALS WITH <span style="color: black;">SOUL</span></h1>
        <h4 class="HeaderTitleh4">Nothing brings people together like good food...</h4>
        <a href="" class="btn">Go to Menu..</a>
    </div>
  </header>
  <div class="service">

    <div class="serviceBox">
        <img src="../assets/img/shipping.png" alt="" class="serImg">
        <h2>FREE DELIVERY</h2>
        <h4>Free on all orders.</h4>
    </div>

    <div class="serviceBox">
        <img src="../assets/img/contact.png" alt="" class="serImg">
        <h2 class="serviceTitle">CONTACT US!</h2>
        <h4 class="serviceText">Keep in touch via email and <br> support system</h4>
    </div>

  </div>
</template>

<script>
export default {

}
</script>

<style>

.service{
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin: 30px;
}

.serviceBox{
    text-align: center;
}

.serImg{
    width: 100px;
}

.HeaderTitle{
    font-size: 100px;
    color:  #EBEDEF ;
}

.HeaderTitleh4{
    font-weight: 400;
    font-size: 30px;
    color:  #EBEDEF ;
}


header{
    display: flex;
    justify-content:left;
    align-items: center;
    width: 100%;
    height: 100vh;
    background-image: url('https://images.pexels.com/photos/1583884/pexels-photo-1583884.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1');
    background-repeat: no-repeat;
    background-size: cover;
    color: whitesmoke;
    clip-path: polygon(0 0, 100% 0, 100% 96%, 0 86%);
}

.headerBox{
    max-width: 700px;
    display: flex;
    justify-content: center;
    align-items: baseline;
    flex-direction: column;
    margin-left: 40px;
}

.btn{
    padding: 10px 20px;
    margin: 10px;
    background-color: yellow;
    color:black;
    border: none;
    border-radius: 5px;
    text-decoration: none;
    font-weight: bold;
    font-size: 20px;
    cursor: pointer;
}

@media screen and (max-width:500px) {
header{

    height: 110vh;
    
}

.HeaderTitle{
    font-size: 80px;
    
}

.HeaderTitleh4{
    display: none;
}


.headerBox{
    width: 300px;
}

.service{
    
    flex-direction: column;

    width: 100%;
    display: flex;
    align-items: center;
    gap: 30px;
    margin: 20px;   
}
.serImg{
    width: 150px;
}
}

</style>