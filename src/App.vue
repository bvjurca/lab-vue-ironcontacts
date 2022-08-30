<template>
  <div id="app">
    <h1>IronContacts</h1>
    <div class="actor-list" v-for="actor in firstFive" :key="actor.id">
      <table class="table">
        <thead></thead>
        <tbody>
          <tr>
            <td>{{contact.name}}</td>
            <td>{{contact.popularity}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import contacts from "./contacts.json";
import { toRefs, reactive, defineComponent } from "vue";

export default defineComponent({
  name: "App",
  setup: () => {
    const actors = contacts;
    const firstFive = reactive(contacts.slice(0, 5));
    return firstFive;
  },
});
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
</style>
