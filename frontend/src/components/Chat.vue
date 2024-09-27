<template>
  <div id="chat-container">
    <ul>
      <li v-for="message in messages">
        <p class="morgana-message" v-if="message.msgsender === Sender.MORGANA">{{ message.text }}</p>
        <p class="user-message" v-else>{{ message.text }}</p>
      </li>
    </ul>
    <form @submit.prevent="sendMessage">
      <input v-model="newMessage" type="text">
    </form>
  </div>
</template>


<script setup lang="ts">
import {ref} from "vue";

const newMessage = ref('');
const messages = ref([]);

enum Sender {
  USER,
  MORGANA
}

function Message(msgsender, text) {
  this.msgsender = msgsender;
  this.text = text;
}

function getMessages() {
  //call api
  if (messages.value.length === 0) {
    messages.value.push(new Message(Sender.MORGANA, "Hello, how can I help you?"));
  }
}

function sendMessage() {
  if (newMessage.value !== '') {
    messages.value.push(new Message(Sender.USER, newMessage.value));
    // send to backend
    newMessage.value = '';
  }
}

getMessages();
</script>


<style>
#chat-container {
  width: 45%;
  text-align: center;
  display: flex;
  flex-direction: column;
  border: 1px solid black;
}

input {
  width: 100%;
  padding: 10px;
  border-radius: 30px;
  color: black;
  border-style: solid;
  box-sizing: border-box;
}

p {
  color: black;
  border-style: solid;
  border-radius: 20px;
  border-width: thin;
  width: 65%;
}

.user-message {
  margin-left: auto;
}

.morgana-message {
  margin-right: 0;
}

ul {
  padding: 0;
}

form {
  margin-top: auto;
}
</style>