<template>
  <div class="container">
    <h1>Comentário</h1>
    <hr />
    <Form v-on:add-comment="addComment" />
    <hr />
    <div class="list-group">
      <p v-if="comments.length <= 0" >Sem Comentários ... </p>
      <Comment
        v-for="(comment, index) in allComments"
        v-bind:key="index"
        v-bind:comment="comment"
        v-bind:index="index"
        v-on:remove-comment="removeComment"
      />
    </div>
  </div>
</template>

<script>

import Comment from "./components/Comment";
import Form from "./components/Form";

export default {
  name: "App",
  components: {
    Comment,
    Form,
  },
  data() {
    return {
      comments: [],
    };
  },
  methods: {
    addComment(comment) {
      this.comments.push({
        name: comment.name,
        message: comment.message,
      });
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        name: comment.name.trim() === "" ? "Anonymous" : comment.name,
      }));
    },
  },
};

</script>