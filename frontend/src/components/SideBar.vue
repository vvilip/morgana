<template>
  <div id="container">
    <h1>Morgana</h1>
    <button id="add-button" @click="addRoom">+</button>
    <ul id="chat-list">
      <li v-for="room in chatRooms">
        <button class="room-button">{{ room.name }}</button>
      </li>
    </ul>
    <div id="footer">
      <button>Settings</button>
      <button v-if="isLightMode" @click="changeColor">Darkmode</button>
      <button v-else @click="changeColor">Lightmode</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import {ref} from "vue";

const isLightMode = ref(true);
const chatRooms = ref([]);

function Room(id, name) {
  this.id = id;
  this.name = name;
}

function changeColor() {
  // Add actual functionality
  isLightMode.value = isLightMode.value !== true;
}

function addRoom(name) {
  // Add backend stuff...
  if (chatRooms.value.length === 12) {
    alert("You have too much open chat-rooms, please close one to open a new one.")
  } else {
    chatRooms.value.push(new Room(0, "New room"));
  }
}

</script>

<style>
* {
  color: white;
}

#container {
  background-color: #821131;
  width: 15%;
  text-align: center;
  margin: 0;
}

button {
  background-color: #C7253E;
  border-style: none;
  font-size: 20px;
  cursor: pointer;
  margin: 10px;
}

button:hover {
  box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
}

#add-button {
  display: inline-block;
  font-size: 30px;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  margin-bottom: 20px;
}

#chat-list {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

#footer {
  position: fixed;
  bottom: 10px;
  width: 15%;
  margin: auto;
}

.room-button {
  width: 80%;
  padding: 3%;
}
</style>