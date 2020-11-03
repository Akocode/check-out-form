<template>
    <h2>Order Summary</h2>
    <div class="container">
        <div class="image">
            <img :src="source">
        </div>
        <div class="details">
            <div class="small">
                <h5>Small Kensington</h5>
                <h5>$995.0</h5>
            </div>
            <h5>Poppy Red Small Classic Grain</h5>
            <div class="standard">
                <h5>Standard ( 1 - 2 working days)</h5>
                <h5>$8.00</h5>
            </div>
        </div>
        <div class="price">
            <h2>Total</h2>
            <h2>$1,003.00</h2>
        </div>
        <div class="btn">
            <button>PLACE ORDER</button>
        </div>
        <div class="order">
            <p>By placing your order you are agreeing to Mulbery's 
                <a href="">Terms of Sale & Privacy Policy</a>
            </p>
        </div>
    </div>
    <div class="norton_image">
        <a href=""><img src="../assets/norton.png" alt="" class="image"></a>
    </div>
</template>

<script>
export default {
    name: "Summary",
}
</script>

<style scoped>
h2{
    font-family: 'montserrat', sans-serif;
    /* font-weight: 100;
    font-size: 0px; */
}
.container{
    background-color: lightgray ;
    margin-top: -6px;
    padding: 20px;
    font-family: 'montserrat', sans-serif;
}

.small{
    display: flex;
    justify-content: space-between;
}

.standard{
    display: flex;
    justify-content: space-between;
}

.price{
    display: flex;
    justify-content: space-between;
    border-top: 1px solid rgb(182, 179, 179);
}

.order{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
}

.btn{
    /* width: 70%; */
    display: flex;
    justify-content: center;
    align-content: center;
}

button:hover{
    cursor: pointer;
}

.norton_image{
    /* background-image: url('../assets/norton.png'); */
}

.image{
    width: 100%;
    height: 100%;
}
</style>