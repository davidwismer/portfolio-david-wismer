<script setup>
import { ref, watchEffect } from 'vue';
import emailjs from 'emailjs-com'

const name = ref('')
const email = ref('')
const message = ref('')
const templateParams = ref({
    name: name.value,
    email: email.value,
    message: message.value
})
//For validation
const validated = ref(false)

async function sendContact() {
    if (validated.value) {
        const templateParams = {
            name: name.value,
            email: email.value,
            message: message.value
        }
        //Send email to david.wismer@heig-vd.ch with name email and message of form
        /* await emailjs.send("service_0vclyoe", "template_tdxxws5", templateParams, "getTfFC6EG71QKEVm") */
        console.log('email envoyé')
        name.value = ''
        email.value = ''
        message.value = ''
        //Reset validation boolean
        validated.value = false
    }
}
const nameFalse = ref(false)
const emailFalse = ref(false)
const messageFalse = ref(false)
async function checkValidation() {
    ///////////////////////////Validation champs vides
    if (name.value == '') nameFalse.value = true
    if (email.value == '') emailFalse.value = true
    if (message.value == '') messageFalse.value = true

    if(!nameFalse.value && !emailFalse.value && !messageFalse.value){
        return validated.value = true
    }else{
        return validated.value = false
    }
}
async function resetValidation(){
    validated.value = false
}
watchEffect(() => {
    name.value
    nameFalse.value=false
});
watchEffect(() => {
    email.value
    emailFalse.value=false
});
watchEffect(() => {
    message.value
    messageFalse.value=false
});
</script>

<template>
    <section class="contact-content">
        <div class="title">Contact me</div>
        <div class="subtitle">Any questions or want to work together?</div>
        <form onsubmit="return false">
            <input type="text" placeholder="Name *" id="name" v-model="name" :class="{ 'nameFalse': nameFalse }" />
            <input type="email" placeholder="Enter email *" id="email" v-model="email"
                :class="{ 'emailFalse': emailFalse }" />
            <textarea placeholder="Your Message *" id="message" cols="30" rows="10" v-model="message"
                :class="{ 'messageFalse': messageFalse }"></textarea>
            <button class="submit" @mouseenter="checkValidation()" @mouseleave="resetValidation()" @click="sendContact()" :class="{ 'submitable': validated }">SUBMIT</button>
        </form>
    </section>
</template>

<style scoped>
section {
    position: fixed;
    width: 100%;
    height: 100%;
    background-color: #373737;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.title {
    font-size: 32px;
    margin-top: 100px;
    margin-bottom: 100px;
}

form {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 600px;
    gap: 5px;
}

input {
    height: 40px;
    width: 100%;
    outline: none;
    background-color: #303030;
    color: white;
    font-family: "League Spartan Regular";
    font-size: 18px;
    border: none;
    padding-left: 10px;
    padding-right: 10px;
}

textarea::placeholder,
input::placeholder {
    color: #C0C0C2;
    opacity: 50%;
}

#message {
    height: 300px;
    width: 100%;
    text-align: start;
    outline: none;
    background-color: #303030;
    color: white;
    font-family: "League Spartan Regular";
    font-size: 18px;
    border: none;
    resize: none;
    padding: 10px;
}

.nameFalse {
    border: solid .5px red;
}

.emailFalse {
    border: solid .5px red;
}

.messageFalse {
    border: solid .5px red !important;
}

.submit {
    width: 100px;
    text-align: center;
    padding: 10px 10px 7px 10px;
    font-family: "League Spartan Regular";
    font-size: 18px;
    color: #ACBABF;
    font-family: "League Spartan Regular";
    border: 1px solid #ACBABF;
    background-color: #373737;
    border-radius: 5px;
    transition: 0.4s;
    margin-top: 5px;
}

.submitable {
    background-color: #ACBABF;
    color: #373737;
    cursor: pointer;
}

@media screen and (max-width: 700px) {
    form {
        width: 350px;
    }
}

@media screen and (max-width: 450px) {
    form {
        width: 250px;
    }

    .title {
        font-size: 24px;
        margin-top: 100px;
        margin-bottom: 50px;
    }

    .subtitle {
        font-size: 14px;
    }
}

@media screen and (max-height: 750px) {
    #message {
        height: 200px;
    }
}
</style>