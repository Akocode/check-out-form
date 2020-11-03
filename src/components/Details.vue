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
                <h4><i class="fas fa-check-circle"></i>Deliver to an address in United Kingdom</h4>
                <a href="">EDIT THIS</a>
            </div>
            <h4>Enter the recipent's details</h4>
            <select id="title" v-model="state.Selectedtitle">
                <option :value="option.value" v-for="(option, index) in state.Selectedoptions" :key="index">
                    {{option.name}}
                </option>
            </select>
            <div class="name">
                <input type="text" placeholder="First Name">
                <input type="text" placeholder="Last Name">
            </div>
            <div class="address">
                <input type="text" placeholder="City" id="address_text">
                <input type="text" placeholder="Postcode" id="address_text">
                <button>FIND ADDRESS</button>
            </div>
            <h4>Or enter it manually here</h4>
                <div class="address_input">
                    <div class="address_long">
                        <input type="text" placeholder="Address Line 1">
                        <input type="text" placeholder="Address Line 2">
                    </div>
                    <div class="address_town">
                        <input type="text" placeholder="Town/City">
                        <input type="text" placeholder="Country(optional)">
                    </div>
                    <input type="text" placeholder="Postcode">
                    <h4 id="question">Enter your contact number <a href=""><i class="fa fa-question-circle" id="question_tag"></i></a></h4>
                    <input type="text" placeholder="Contact number">
                </div>
                <div class="last_div">
                    <div class="confirm_divbtn">
                        <button id="botton_confirm">CONFIRM DETAILS</button>
                    </div>
                </div>
        </div>
        <div class="base_payment">
            <h5>Payment</h5>
        </div>
    </div>
</template>

<script>
import { reactive } from 'vue';
export default {
    name: "Details",
    setup(){
        const state = reactive({
            Selectedtitle: 'Mr',
            Selectedoptions: [
                {value: 'Mr', name: 'Mr'},
                {value: 'Mrs', name: 'Mrs'},
                {value: 'Miss', name: 'Miss'},
                {value: 'Ms', name: 'Ms'},
                {value: 'Dr.', name: 'Dr.'},
                {value: 'Other', name: 'Other'},
            ],
        });

        return{
            state,
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

#question_tag{
    /* margin-left: 1px; */
}


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