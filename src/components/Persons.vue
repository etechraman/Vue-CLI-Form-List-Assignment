<template>
  <div>
    <ul>
      <li v-for="(item, index) in data" v-bind:key="index">
        <span>{{ item }}</span>
        <a href="#" v-on:click.prevent="$emit('delete-item', index)">Delete</a>
        <a href="#" v-on:click.prevent="$emit('edit-item', index)">Edit</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Data",
  props: ["data"],
};
</script>

<style>
li {
  border: 1px solid;
  padding: 5px;
}
li a {
  font-size: 14px;
  float: right;
  padding: 5px;
}
</style>
