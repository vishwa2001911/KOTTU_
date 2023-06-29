<template>
  <div class="About">
    <div class="AboutBox">
        <img src="https://images.pexels.com/photos/1527603/pexels-photo-1527603.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="" class="AboutImg">
        <div class="AboutText">
            <h1 class="aboutTitle">
                GET YOUR FOODS <span style="color: black;">NOW!</span>
            </h1>
            <button class="MoreOptions">DISCOVER MORE</button>
        </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>

.About{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
}

.AboutBox{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    
}

.AboutImg, .AboutText{
    width: 50%;
    height: 400px;
    margin: 10px;
    
}

.AboutText{
    background-color: yellow;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    font-size: 30px;
    color: whitesmoke;
    font-weight: bold;
    position: relative;
}

.MoreOptions{
    position: absolute;
    bottom: 35px;
    left: 35px;
    font-size: 25px;
    padding: 20px;
    border: solid black 3px;
    background-color: whitesmoke;
    font-weight: bold;
    cursor: pointer;
    transition: 0.4s;
}

.MoreOptions:hover{
    background-color: #E67E22 ;
    border-color: #E67E22 ;
}

.aboutTitle{
    margin-left: 30px;
}
@media screen  and (max-width: 900px){
    .AboutBox{
        flex-direction: column;
    }
    .AboutImg{
        display: none;
    }
    
    .AboutText{
    width: 100%;
    height: 700px;
    font-size: 48px;
    padding-left: 0;
    
}
}


</style>