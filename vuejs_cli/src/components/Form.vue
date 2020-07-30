<template>
  <div class="form-group form-todo">
    <p>
      <input type="text" class="form-control" placeholder="nome" v-model="name" />
    </p>
    <p>
      <textarea class="form-control" placeholder="Comentario" v-model="message"></textarea>
    </p>
    <button v-on:click="addComment" type="button" class="btn btn-primary">Comentar</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      if (this.message.trim() === "") {
        return;
      }
      this.$emit("add-comment", {
        name: this.name,
        message: this.message
      });

      this.name = "";
      this.message = "";
    },
  },
};
</script>
