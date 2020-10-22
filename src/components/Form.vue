<template>
  <div id="submitForm">
    <p>Type Something..</p>
    <i>Press enter</i>
    <br />
    <form v-on:submit.prevent>
      <input
        v-on:keypress="submit"
        v-on:click="submit"
        type="text"
        v-model="text"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      text: "",
    };
  },
  watch: {
    name(newName) {
      this.text = newName;
    },
  },
  props: {
    name: {
      type: String,
      require: true,
    },
    editIndex: {
      type: Number,
      require: true,
    },
  },
  methods: {
    submit(e) {
      if (e.keyCode === 13) {
        if (this.editIndex !== -1) {
          if (this.text.length !== 0) {
            this.$emit("edit-item", {
              name: this.text,
              editIndex: this.editIndex,
            });
          }
        } else {
          this.$emit("submit-item", this.text);
        }
        this.text = "";
      }
    },
  },
};
</script>
