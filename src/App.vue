<template>
  <div>
    <h1>IronContacts</h1>
    <div class="btns">
      <button @click="randActor">Add Random Contact</button>
      <button @click="popSort">Sort By Popularity</button>
      <button @click="alphaSort">Sort By Name</button>
    </div>
    <div class="head">
      <h2>Picture</h2>
      <h2>Name</h2>
      <h2>Popularity</h2>
      <h2>Won Oscar</h2>
      <h2>Won Emmy</h2>
      <h2>Actions</h2>
    </div>
    <div class="contact" v-for="contact in firstFive" :key="contact.id">
      <img :src="contact.pictureUrl" :alt="contact.name" width="50" />
      <div>{{ contact.name }}</div>
      <div>{{ contact.popularity.toFixed(2) }}</div>
      <div v-if="contact.wonOscar">WON</div>
      <div v-else></div>
      <div v-if="contact.wonEmmy">WON</div>
      <div v-else></div>
      <div>
        <button @click="delActor(contact)">Delete</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import contacts from "./contacts.json";
import { reactive } from "vue";
const actors = reactive(contacts);
const firstFive = reactive(contacts.slice(0, 5)); 
const diff = reactive(contacts.slice(5)); 
function randActor() {
  const rand = Math.floor(Math.random() * diff.length);
  firstFive.push(diff[rand]); 
  diff.splice(rand, 1); 
}
function popSort() {
  firstFive.sort((a, b) => (a.popularity < b.popularity ? 1 : -1));
}
function alphaSort() {
  firstFive.sort((a, b) => (a.name > b.name ? 1 : -1));
}
function delActor(contact) {
  const index = firstFive.indexOf(contact);
  firstFive.splice(index, 1);
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.head,
.contact, .btns {
  display: flex;
  margin: 15px;
  align-items: center;
  justify-content: center;
}
.contact img,
.contact div,
.head h2 {
  width: 7vw;
}
</style>