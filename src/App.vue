<template>
  <div id="app" @click.self="clear()">
    <img alt="Vue logo" src="./assets/logo.png" />
    <Form
      :edit-index="editIndex"
      :name="name"
      @edit-item="edit"
      @submit-item="submit"
    />
    <Persons :data="data" @delete-item="deleteItem" @edit-item="editItem" />
  </div>
</template>

<script>
import Persons from "./components/Persons.vue";
import Form from "./components/Form.vue";
import Vue from "vue";
export default {
  name: "App",
  components: {
    Persons,
    Form,
  },
  data() {
    return {
      data: [],
      name: "",
      editIndex: -1,
    };
  },
  methods: {
    edit(obj) {
      var { name, editIndex } = obj;
      Vue.set(this.data, editIndex, name);
      this.name = "";
      this.editIndex = -1;
      console.log("editing");
    },
    submit(name) {
      console.log("Submitted");
      this.data.push(name);
      this.name = "";
    },
    deleteItem(index) {
      this.data.splice(index, 1);
      console.log("deleted");
    },
    editItem(index) {
      this.editIndex = index;
      this.name = this.data[index];
    },
    clear() {
      console.log("Clicked");
      this.editIndex = -1;
    },
  },
};
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
