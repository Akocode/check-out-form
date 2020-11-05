<template>
<div class="container">
  <h1 class="checkout">Checkout</h1>
  <h5 class="checkout_message">You are checking out as a guest with the email
     <b v-bind="email"> {{state.email}} </b>
    <a href="" class="message_link" @click.prevent="editMail">Edit this</a>
  </h5>
  <div class="another_container">
    <div class="details">
      <Details />
    </div>
    <div class="payment">
      <Summary />
    </div>
  </div>
</div>
<button type="button" class="btn" @click="showModal"> Open Modal! </button>
<Modal v-show="state.isModalVisible" @close="closeModal" @save="saveModal"/>
</template>

<script>
import { reactive } from 'vue';
import Modal from './components/Modal';
import Details from './components/Details';
import Summary from './components/Summary';
export default {
  name: 'App',
  components: {
    Details,
    Summary,
    Modal,
  },
  setup(){
    const state = reactive({
      email: ' email.this@email.com ',
      isModalVisible: false,
    });

    function editMail(){
      var mail = prompt('Provide the new mail');
      if (mail.includes("@") && mail.includes(".com")) {
        state.email = mail;
      } else{
        alert("invalid email");
      }
    }

    function showModal(){
      state.isModalVisible = true;
    }

    function closeModal(){
      state.isModalVisible = false;
    }

    function saveModal(){
      alert("thank you");
      state.isModalVisible = false;
    }

    return{
      state,
      editMail,
      showModal,
      closeModal,
      saveModal,
    }
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

b{
  font-weight: 1000;
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
