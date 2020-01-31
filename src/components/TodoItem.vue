<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed" />
      <strong>{{index + 1}}</strong>
      {{todo.title | uppercase}}
      <button class="remove" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </span>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object
    },
    index: Number
  }, 
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
};
</script>

<style scoped>
    li {
        border: 1px solid #000;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
        position: relative;
    }

    .remove {
        background: red;
        color: white;
        border: 0;
        border-radius: 50%;
        cursor: pointer;
        outline: 0;
        font-weight: bold;
        position: absolute;
        right: 30px;
    }

    .done {
        text-decoration: line-through;
    }

    input {
        margin-right: 1rem;
    }
</style>