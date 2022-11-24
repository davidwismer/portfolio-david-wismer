<script setup>
import { ref } from 'vue';
import emailjs from 'emailjs-com'

const name = ref('')
const email = ref('')
const message = ref('')
const templateParams = ref({
    name: name.value,
    email: email.value,
    message: message.value
})
async function sendContact() {
    const templateParams = {
        name: name.value,
        email: email.value,
        message: message.value
    }
    //Send email to david.wismer@heig-vd.ch with name email and message of form
    await emailjs.send("service_0vclyoe", "template_tdxxws5", templateParams, "getTfFC6EG71QKEVm")
    name.value = ''
    email.value = ''
    message.value = ''
}
</script>

<template>
    <section class="contact-content">
        <div class="title">Contact me</div>
        <div class="subtitle">Any questions or want to work together?</div>
        <form onsubmit="return false">
            <input type="text" placeholder="Name" id="name" v-model="name" />
            <input type="email" placeholder="Enter email" id="email" v-model="email" />
            <textarea placeholder="Your Message" id="message" cols="30" rows="10" v-model="message"></textarea>
            <button class="submit" @click="sendContact()">SUBMIT</button>
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
    cursor: pointer;
    transition: 0.4s;
    margin-top: 5px;
}

.submit:hover {
    background-color: #ACBABF;
    color: #373737;
}
</style>