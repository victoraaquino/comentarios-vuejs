<template>
  <div class="list-group-item">
    <span class="comment__author">
      Autor:
      <strong>{{comment.name}}</strong>
    </span>
    <p>{{comment.message}}</p>
    <div>
      <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
    </div>
  </div>
</template>

<script>
export default {
  props: ['comment', 'index'],
   methods: {
    removeComment(index) {
      this.$emit('remove-comment', index);
    },
  }
};
</script>
