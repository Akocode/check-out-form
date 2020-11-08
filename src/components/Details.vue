<template>
    <h2 class="heading_message">Please complete your details</h2>
    <div class="container">
        <div class="packaging_class">
            <div class="packaging">
                <h2>Packaging</h2>
            </div>
            <div class="standard">
                <h4><i class="fas fa-check-circle"></i>Standard</h4>
                <a class="package_link" href="">EDIT THIS</a>
            </div>
            <div class="no_gift">
                <h4><i class="fas fa-check-circle"></i>No gift message</h4>
                <a class="package_link" href="">EDIT THIS</a>
            </div>
        </div>
        <div class="delivery">
            <h2>Delivery</h2>
            <div class="deliver_uk">
                <h4 id="delivery_letter"><i class="fas fa-check-circle"></i>Deliver to an address in United Kingdom</h4>
                <a href="">EDIT THIS</a>
            </div>
            <h4>Enter the recipent's details</h4>
            <select id="title" v-model="state.Selectedtitle">
                <option :value="option.value" v-for="(option, index) in state.Selectedoptions" :key="index">
                    {{option.name}}
                </option>
            </select>
            <div class="name">
                <input type="text" placeholder="First Name" v-model="state.first_name">
                <input type="text" placeholder="Last Name" v-model="state.last_name">
            </div>
            <div class="address">
                <input type="text" placeholder="Input Your Address/Postcode" id="address_text" v-model="state.postcode">
                <select id="title" v-if="state.postCodeSearched" v-model="state.selectedAddress" v-on:change="emitAddress">
                    <option value="" selected>Please select</option>
                    <option :value="item.summaryline" v-for="(item, index) in state.addressList" :key="index">
                        {{item.summaryline}}
                    </option>
                </select>
                <p v-if="state.noResults">Sorry, we were unable to find that post-code</p>
                <button v-on:click="addressLookUp">FIND ADDRESS</button>
            </div>
            <h4>Or enter it manually here</h4>
                <div class="address_input" v-on:addresschanged="updateAddress">
                    <div class="address_long">
                        <input type="text" placeholder="Address Line 1" v-model="state.line_1" disabled>
                        <input type="text" placeholder="Address Line 2" v-model="state.line_2" disabled>
                    </div>
                    <div class="address_town">
                        <input type="text" placeholder="Town/City" v-model="state.city" disabled>
                        <input type="text" placeholder="Country(optional)" v-model="state.country" disabled>
                    </div>
                    <input type="text" placeholder="Postcode" v-model="state.postal" disabled>
                    <h4 id="question">Enter your contact number <a href=""><i class="fa fa-question-circle" id="question_tag"></i></a></h4>
                    <input type="text" placeholder="Contact number" v-model="state.number">
                </div>
                <div class="last_div">
                    <div class="confirm_divbtn">
                        <button id="botton_confirm" @click="showModal">CONFIRM DETAILS</button>
                    </div>
                </div>
        </div>
        <div class="base_payment">
            <h5>Payment</h5>
        </div>
    </div>
    <Modal v-show="state.isModalVisible" 
        @close="closeModal"
        @save="saveModal" 
        :first_name = "state.first_name"
        :last_name = "state.last_name"
        :number = "state.number"
        :email = "state.email"
     />
</template>

<script>
import Modal from './Modal';
import { reactive } from 'vue';
// import {axios} from 'axios';
export default {
    name: "Details",
    components: {
        Modal,
    },
    setup(ctx){
        const state = reactive({
            postal: '',
            first_name: '',
            last_name: '',
            line_1: '',
            line_2: '',
            city: '',
            country: '',
            number: '',
            Selectedtitle: 'Mr',
            Selectedoptions: [
                {value: 'Mr', name: 'Mr'},
                {value: 'Mrs', name: 'Mrs'},
                {value: 'Miss', name: 'Miss'},
                {value: 'Ms', name: 'Ms'},
                {value: 'Dr.', name: 'Dr.'},
                {value: 'Other', name: 'Other'},
            ],
            isSearching: false,
            postcode: '',
            addressList: [],
            selectedAddress: '',
            postCodeSearched: false,
            noResults: false
        });

        function addressLookUp(){
            // var proxyUrl = 'https://cors-anywhere.herokuapp.com/';
            // var targetUrl = `https://api.getAddress.io/find/${state.postcode}?api-key=ndnyWw3hkkCuYMDYtpR4VQ28999`
            fetch(`https://ws.postcoder.com/pcw/PCWZJ-7426G-4FXY3-VRF33/address/uk/${state.postcode}`)
                .then(response => { 
                    state.addressList = response.json()
                    state.postCodeSearched = true
                    state.noResults = false
            })
            .catch(error => {
                state.noResults = true
                console.log(error);
            })
        }

        function emitAddress() {
            if(state.selectedAddress != '') {
                ctx.$emit('addresschanged', state.selectedAddress)
            }
        }

        function updateAddress(payLoad) {   
            let addressArray = payLoad.split(",")
            // this.house = addressArray[0]
            // this.building = addressArray[1]
            // this.street = addressArray[2]
            // this.suburb = addressArray[4]
            // this.city = addressArray[5]
            state.line_1 = addressArray[0][0]
            state.line_2 = addressArray[0][1]
            state.city = addressArray[5]
            state.country = addressArray[13]
        }

        function showModal(){
            state.isModalVisible = true;
            // state.first_name = 'no name'
        }

        function closeModal(){
            state.isModalVisible = false;
        }

        function saveModal(){
            alert("Thank you! You can proceed to place your order");
            state.isModalVisible = false;
        }

        return{
            state,
            addressLookUp,
            emitAddress,
            updateAddress,
            showModal,
            closeModal,
            saveModal,
        }
    },
}
</script>

<style scoped>
h2{
    font-family: 'montserrat', sans-serif;
}
.container{
    padding: 0;
    margin-top: -6px;
    min-height: 100vh;
    border: 1px solid rgb(236, 230, 230);
    font-family: 'montserrat', sans-serif;
}

.packaging_class{
    background-color: lightgrey;
    margin: auto;
    padding-left: 30px;
    padding-right: 30px;
}

.packaging{
    display: flex;
}

.standard{
    display: flex;
    justify-content: space-between;
    align-items: baseline;
}

i{
    margin-right: 20px;
}

.no_gift{
    border-top: 1px solid rgb(182, 179, 179);
    display: flex;
    justify-content: space-between;
    align-items: baseline;
}

.delivery{
    padding-left: 30px;
    padding-right: 30px;
    padding-bottom: 10px;
}

.deliver_uk{
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    border-bottom: 1px solid rgb(182, 179, 179);
}

#delivery_letter{
    display: flex;
    flex-direction: row;
}

input{
    margin: inherit;
    justify-content: space-evenly;
    background-color: rgb(226, 222, 222);
    height: 25px;
    display: inline-flex;
    justify-content: space-between;
    padding-left: 10px;
}

#title{
    width: 150px;
    height: 30px;
    margin-bottom: 10px;
    margin-top: -5px;
}

.name{
    display: flex;
    justify-content: space-between;
}

.address{
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
    align-items: baseline;
    background-color: lightgray;
    padding: 10px;
}

 .address_input{
    margin-bottom: 5px;
}

#address_text{
    background-color: white;
    width: 60%;
}

.address_long{
    display: flex;
    flex-direction: column;
    width: 70%;
    margin: 0px 0px 5px 0px;
}

.address_town{
    /* width: 70%; */
    display: flex;
    justify-content: space-between;
    width: 70%;
    margin-bottom: 5px;
}

button{
    display: inline-block;
    justify-items: center;
    height: 35px;
    width: 120px;
    background-color: rgb(88, 87, 87);
    color: white;
}

button:hover{
    cursor: pointer;
}

#question{
    margin: 5px 15px 5px 0px;
    font-weight: 100;
}

/* #question_tag{
    margin-left: 1px;
} */


.last_div{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.confirm_divbtn{
    display: flex;
    justify-content: flex-end;
}

#botton_confirm{
    margin-bottom: 10px;
    width: 150px;
    background-color: rgb(26, 25, 25);
    color: white;
}

.base_payment{
    padding: 5px 0px 5px 30px;
    background-color: rgb(226, 222, 222);

}

</style>