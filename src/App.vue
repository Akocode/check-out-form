<template>
<div class="container">
  <h1 class="checkout">Checkout</h1>
  <h5 class="checkout_message">You are checking out as a guest with email email.this@email.com <a href="" class="message_link">Edit this</a></h5>
  <div class="another_container">
    <div class="details">
      <Details />
    </div>
    <div class="payment">
      <Summary />
    </div>
  </div>
</div>
</template>

<script>
import Details from './components/Details';
import Summary from './components/Summary';
export default {
  name: 'App',
  components: {
    Details,
    Summary,
  }
}
</script>

<style scoped>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  min-height: 100vh;
} */

/* *{
  margin: 0;
  padding: 0; */
  /* box-sizing: border-box; */
/* } */

h1,h5{
  text-align: center;
  font-family: 'montserrat', sans-serif;
}

body {
  font-family: 'montserrat', sans-serif;
  /* font-family: 'montserrat', sans-serif; */
  /* min-height: 100vh; */
  
}

.another_container{
  display: grid;
  grid-template-columns: 3fr 1fr;
    min-width: 100vh;
    grid-gap: 20px;
    padding: 5px 1%;
    position: relative;
}
</style>
