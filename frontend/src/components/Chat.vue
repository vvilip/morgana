<template>
  <div id="chat-container">
    <form @submit.prevent="sendMessage">
      <input v-model="newMessage" type="text">
    </form>
    <ul>
      <li v-for="message in messages">
        <p>{{ message.text }}</p>
      </li>
    </ul>
  </div>
</template>


<script setup lang="ts">
import {ref} from "vue";

const newMessage = ref('');
const messages = ref([]);

function Message(user, text) {
  this.user = user;
  this.text = text;
}

function getMessages() {
  //call api
  if (messages.value.length === 0) {
    messages.value.push(new Message("Morgana", "Hello, how can I help you?"));
  }
}

function sendMessage() {
  if (newMessage.value !== '') {
    messages.value.push(new Message("User", newMessage.value));
    // send to backend
    newMessage.value = '';
  }
}

getMessages();
</script>


<style>
#chat-container {
  width: 40%;
  text-align: center;
}

input {
  width: 40%;
  position: fixed;
  bottom: 20px;
  padding: 10px;
  border-style: solid;
  border-radius: 30px;
  color: black;
}

p {
  color: black;
  border-style: solid;
  border-radius: 20px;
  border-width: thin;
  width: 65%;
}
</style>